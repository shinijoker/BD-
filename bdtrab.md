# BD-script sql
CREATE TABLE  cliente (
            cpf varchar(11) not null,
            cnome varchar(40) not null,
            endereço(50) not null,
            fone int not null,
            PRIMARY KEY (cpf)
);

CREATE TABLE  medico (
            crm varchar(11) not null,
            mednome varchar(30) not null,
            fone int not null,
            PRIMARY KEY (crm)
);

CREATE TABLE consulta(
            crm varchar(11) not null,
            cpf varchar(11) not null,
            FOREIGN KEY (crm) REFERENCES medico (crm),
            FOREIGN KEY (cpf) REFERENCES fabricante (cpf)
);

CREATE TABLE medicamento(
            mcod int not null,
            mnome varchar(30) not null,
            tarja varchar(9) not null,
            mestoque int not null,
            mpreço float not null,
            PRIMARY KEY (mcod)
);

CREATE TABLE produto(
            pcod int not null,
            pnome varchar(30),
            pestoque int,
            ppreço float,
            PRIMARY KEY (cod)
);
CREATE TABLE farmacia(
            cnpj varchar(13) not null,
            fnome varchar(30) not null,
            PRIMARY KEY (cnpj)
);

CREATE TABLE farmacia_medicamento(
            cnpj varchar(13) not null,
            mcod int not null,
            FOREIGN KEY (cnpj) REFERENCES farmacia (cnpj),
            FOREIGN KEY (mcod) REFERENCES medicamento (mcod)
);

CREATE TABLE farmacia_produto(
            cnpj varchar(13) not null,
            pcod int not null,
            FOREIGN KEY (cnpj) REFERENCES farmacia (cnpj),
            FOREIGN KEY (pcod) REFERENCES produto (pcod)
);

CREATE TABLE cliente_medicamento(
            cpf varchar(11) not null,
            mcod int not null,
            data varchar(8) not null,
            FOREIGN KEY (cpf) REFERENCES cliente (cpf),
            FOREIGN KEY (mcod) REFERENCES medicamento (mcod)
);

CREATE TABLE cliente_produto(
            cpf varchar(11) not null,
            pcod int not null,
            data varchar(8) not null,
            FOREIGN KEY (cpf) REFERENCES cliente (cpf),
            FOREIGN KEY (pcod) REFERENCES produto (pcod)
);
--popula as tabelas

insert into cliente (cpf, cnome, endereço, fone) values 
			('16366952132', 'wagner', 'rua amaral do gado, n811', 33224455),
			('29283754220', 'Robson_v1d4_lok4', 'rua amaral do gado, n820', 33652455);
      
insert into medico (crm, mednome, fone) values 
			(16366952, 'Rogerio Vilela', 33245580),
			(292830, 'Cleiton_v1d4_lok4', 33652435);			

insert into consulta (crm, cpf) values 
			(16366952, '16366952132'),
			(292830, '29283754220');
      
insert into medicamento (mcod, mnome, tarja, mestoque, mpreço) values
      (142, 'placebo', 'preta', 20, 13.99),
      (188, 'ASS-infantil', 'preta', 30, 21.99),
      (666, 'gardenal', 'verde', 50, 15.00);
      
insert into produto (pcod, pnome, pestoque, ppreço) values
      (255, 'shampoo clearmen', 5, 25.99),
      (187, 'desodorante axe', 7, 17.99),
      (843, 'cortador de unhas', 3, 7);
      
insert into farmacia (cnpj, fnome) values
      ('99809436000193', 'farmacia popular do lucas');
      
insert into farmacia_medicamento(cnpj, mcod) values
      ('99809436000193', 142),
      ('99809436000193', 188),
      ('99809436000193', 666);

insert into farmacia_produto(cnpj, pcod) values
      ('99809436000193', 255),
      ('99809436000193', 187),
      ('99809436000193', 843);
      
insert into cliente_medicamento(cpf, mcod, data) values
      ('16366952132', 142, '12.12.12'),
      ('29283754220', 187, '11.05.17');

insert into cliente_produto(cpf, pcod, data) values
      ('16366952132', 255, '12.12.12'),
      ('29283754220', 843, '11.05.17');
