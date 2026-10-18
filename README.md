#Erros encontrados - Thiago Vilela para a disciplina de Programação Web I

#Professor: William Firmino


-- ERROS:


Erro 1:
#ERRO: Model aluno possui um construtor com um atributo this.ra = dados.curso();

#CORREÇÃO: this.ra = dados.ra();

#COMO ENCONTREI: Abrindo o model Aluno

ERRO 2:
#ERRO: Somente uma dependência foi colocada no pom.xml para o h2.console, que impossibilita que o h2-console rode.

#CORREÇÃO: ADICIONAR a seguinte dependência:

<!-- <dependency>
      		<groupId>org.springframework.boot</groupId>
      		<artifactId>spring-boot-h2console</artifactId>
</dependency> -->

#COMO ENCONTREI: Ao tentar rodar o servidor, interpretando o terminal e comparando com o nosso projeto que temos em aula

ERRO 3:
#ERRO: o scope do h2 estava como "test" e não como "runtime" 

#COMO ENCONTREI: Ao abrir o pom.xml e comparando com o projeto feito em aula.

#CORREÇÃO: Trocar de "test" para "runtime"

ERRO 4:

#ERRO: spring.jpa.hibernate.ddl-auto=none e jwt.secret impediam que o banco fosse criado no h2.console

#CORREÇÃO: Apagar essas linhas

#COMO ENCONTREI: Ao tentar testar os endpoints, verifiquei que sempre dava erro 500 e falava que a tabela não havia sido criada... abri o h2 e vi que estava tudo vazio, fazer isso resolveu o problema.

ERRO 5:

#ERRO: Problema no PUT de Aluno.

#CORREÇÃO: Inserir a anotação @Transactional no método da classe controller

#COMO ENCONTREI: Ao abrir a classe controller do projeto, verifiquei que o método atualizar não continha a anotação, o que acabava fazendo com que os dados não persistisse no banco

ERRO 6:

#ERRO: Problema no POST de Professor

#CORREÇÃO: Inserir a assinatura @GeneratedValue

#COMO ENCONTREI: Ao testar a requisição post para cadastrar o professor, apareceu a seguinte mensagem: 

<!-- "message": "Identifier of entity 'com.github.app.model.professor.Professor' must be manually assigned before calling 'persist()'", -->


ERRO 7:

#ERRO: POST DE Matricula 

#CORREÇÃO: alterar o campo do DTO que recebe o id de aluno para alunoId, como o JSON espera! Tive que alterar também no controller

#COMO ENCONTREI: olhando o corpo da requisição


ERRO 8:

#ERRO: Cardinalidade de aluno

#CORREÇÃO Alterar a anotação @OneToOne para @ManyToOne na matricula para permitir que o aluno possa ter mais de uma matrícula vinculada a ele no sistema.

#COMO ENCONTREI: Lendo o enunciado da prova, reparei que era uma exigência que o aluno pudesse ter mais de uma matrícula vinculada a ele(os endpoints estavam todos funcionando)