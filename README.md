# Criando uma RestAPI no Heroku

Todo processo será feito via terminal.


___

### __1. Dependências__
1. Crie uma conta no [Heroku](https://www.heroku.com/). _Caso já tenha ignore!_

2. Baixe o heroku cli [clique aqui](https://devcenter.heroku.com/articles/heroku-cli#install-the-heroku-cli)

---

### __2. Depois de ter instalado _HEROKU CLI_ Abra o terminal__
- Windows: Abra o Powersh como administrador.
    ![Powersh](/img/powershell.jpeg)

- Linux/Mac: Abra o terminal
    ![terminal](/img/terminal.png)

---

### __3. Execute os comandos abaixo no terminal:__

Substitua o `{APP_NAME}` pelo nome do seu app!


#### 1. Faça login no Heroku, esse comando irá abrir uma aba do navegador para voçê se logar no Heroku.

- Comando
    ```sh
    heroku login
    ```
- Veja resultado no navegador
    ![](/img/step1.png)

- Veja o resultado após o login no terminal
    ![](/img/step2.png)

#### 2. Crie um app no Heroku.

- Comando
    ```sh
    heroku create {APP_NAME} 
    ```
- Veja resultado na interface do Heroku, entre no app criado.
    ![](/img/step4.png)

- Veja o resultado no terminal
    ![](/img/step3.png)

#### 3. Adicione o Buildpack.

- Comando
    ```sh
    heroku buildpacks:set https://github.com/PostgREST/postgrest-heroku --app={APP_NAME} 
    ```

- Veja resultado na interface do Heroku no app criado, em **settings**.
    ![](/img/step5.png)

- Veja o resultado no terminal
    ![](/img/step6.png)

#### 4. Adcionar o Postgres versão 12 no projeto usando AddOn:

- Comando
    ```sh
    heroku addons:create heroku-postgresql:hobby-dev --version=12 --app={APP_NAME}
    ```
- Veja resultado na interface do Heroku no app criado, em **Overview**.
    ![](/img/step7.png)

- Veja o resultado no terminal
    ![](/img/step8.png)

#### 5. Crie as variáveis de ambiente.

- Via interface do Heroku -> Overview -> Abra o Postgres em outra aba do navegador.
    ![](/img/step9.png)

- No Postgres, clique em Settings -> View Crendentials.
    ![](/img/step10.png)

- Copie os valores abaixo
    * User
    * URI

- **Comando**, altere os valores ({User} e {URI}) pelos valores copiados no passo anterior.

    ```sh
    # altere a {URI} E {APP_NAME}
    heroku config:set DB_URI={URI} --app={APP_NAME}
    # altere a {USER} E {APP_NAME}
    heroku config:set DB_ANON_ROLE={User} --app={APP_NAME}
    # altere o {APP_NAME}
    heroku config:set DB_SCHEMA=public --app={APP_NAME}
    # altere o {APP_NAME}
    heroku config:set POSTGREST_VER=5.1.0 --app={APP_NAME}
    ```

- Veja resultado na interface do Heroku no app criado, em **Settings**.
    ![](/img/step11.png)

- Veja o resultado no terminal
    ![](/img/step12.png)

#### 6. Conecte-se ao banco de dados usando PGAdmin e crie uma ou mais tabelas e adicione algumas linhas.

__... Isso é por sua conta!!!!!!!!!__


#### 7. Faça o fork do repositório abaixo.
* Repo: https://github.com/PostgREST/postgrest


#### 8. Via Interface do Heroku, connect o repositório que você "clonou" via fork.

- Heroku ->  Deploy -> Github
    ![](/img/step13.png)


#### 9. Via Interface do Heroku, após conectar o Repo faça o deploy clicando no botão "Deploy Branch".

- Deploy
![](/img/step14.png)


## Acesse o seu App do Heroku
