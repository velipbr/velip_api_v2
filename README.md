# Project: API Velip V2 - Manual
## Exemplos em diversas linguagens

Pode ver  esse manual  no link https://api.velip.com.br via POSTMAN 
No menú superior do manual POSTMAN  você poderá selecionar a linguagem de programação desejada para ver os exemplos . Também poderá copiar todos os exemplos no seu POSTMAN.

<img src="https://content.pstmn.io/b44386c8-25da-4ae9-b8c9-cdb2a0334a45/aW1hZ2UucG5n" width="1691" height="432">

Nos capitulos de cada API poderá também vizualizar diversos exemplos mais utilizados. Caso não encontre o seu caso solicite para suporte@velip.com.br  

<img src="https://content.pstmn.io/bcbe0778-3291-4b2b-9844-5265e2d1a532/aW1hZ2UucG5n" alt="" height="579" width="1460">

## Usos

1. **Torpedo de voz** - Envio de mensagens de voz (torpedo de voz) por telefone em envios individuais ou em lote, com áudios gerados por TTS (Text to Speech) ou pré-gravados. As ligações podem ser atendidas por robôs de atendimento em fluxos conversacionais (IA-NLP) por voz ou teclado (DTMF).
2. **Interconectar 2 destinos por telefone** mantendo a privacidade dos números.
3. **Envio de SMS** individuais ou em lote
4. **Gerar áudio**s por TTS ou por gravação.
    

<h2>Possibilidades</h2>

Com a VELIP, você pode:

<ul><li><p>Disparar mensagem de voz por telefone individuais</p></li><li><p>Disparar mensagem de voz por telefone em lote</p></li><li><p>Disparar mensagem de voz atendidas por robôs de fluxo estruturados (voz ou dtmf)</p></li><li><p>Disparar mensagem de voz atendidas por robôs conversacionais (voz)</p></li><li><p>Unir dois destinos em uma conversa mantendo privacidade dos números</p></li><li><p>Transbordar qualquer ligação para um call center via STFC ou Voip</p></li><li><p>Transbordar qualquer ligação para um atendente remoto em nosso frontend web (Call center em nuvem)</p></li><li><p>Enviar base de destinos por JSON ou arquivo csv</p></li><li><p>Gerar áudios por diversos TTS de alta qualidade</p></li><li><p>Enviar áudios pré-gravados</p></li><li><p>Disparar SMS em conjunção com torpedos de voz</p></li><li><p>Transcrever áudios e gerar respostas de áudio para uso em robôs por voz. Por ex., mensagens de áudio no WhatsApp</p></li></ul>

Após os envios, você poderá:

<ul><li><p>Receber status da requisição no retorno da solicitação</p></li><li><p>Webhook - Receber dados gerais ao final de cada ligação</p></li><li><p>Recebe relatórios automáticos consolidados via FTP, GC Storage, Amazon S3</p></li><li><p>Consultar via APIs os dados das ligações e campanhas</p></li><li><p>Verificar em tempo real todas informações pelo frontend web de controle</p></li><li><p>Emitir relatórios personalizados</p></li></ul>

<h1>REST</h1>

APIs REST normalmente utilizam POST. A função a ser ativada é dada pela URL acionada.

**Encoding: utf-8**

Os parâmetros devem ser enviados no corpo da requisição em JSON e el alguns casos por parâmetros na URL.  
Os retornos serão em JSON conforme detalhado em cada API

<h1>Firewall</h1>

O IP de nosso ponto de presença para você encaminhar uma requisição é **35.241.2.50 porta 443** ou se usar **IPV6: 2600:1901:0:8e18::**  
(https) que corresponde ao [https://vox.velip.com.br](https://vox.velip.com.br)

Se utilizar Call Backs (retorno do status ao final da ligação) eles são encaminhados pelos seguintes IPs :

**35.232.103.91**

**35.184.30.236**

**Portas: 443** (HTTPS - TLS >=1.2 )

<h1>Acesso HTTPS - Ponto de presença</h1>

Para utilização, é necessário uma conta ativa na Velip: [https://www.velip.com.br](https://www.velip.com.br)

**URL: vox.velip.com.br**

**Protocolo: https**

**Ponto de presença URI:**

[https://vox.velip.com.br/api/v2/](https://vox.velip.com.br/api/v2/)

Exemplo para API MakeTTSCall:

[**https://vox.velip.com.br/api/v2/MakeTTSCall**](https://vox.velip.com.br/api/v2/MakeTTSCall)

<h1>Headers</h1>

As requisições devem conter no cabeçalho:

_**Content-Type: application/json**_

**Authorization : Bearer YOURS_TOKEN**

<h1>Autenticação</h1>

As APIs VELIP utilizam TOKEN de autenticação que podem ser permanentes e gerados na area logado do painel de controle ou temporários gerados pela API GetUserID.

Deverá incluir no headers da consulta:  
_**Authorization : Bearer YOURS_TOKEN**_

OPCIONALMENTE pode informar o token :  
a) No header incluir 'Authorization: {token}'  
b) Incluir no JSON "tsid":"{token}"

**1\. GERAR TOKEN permanente**

Na área logada do painel de controle no menú : API - CONFiGURA - TOKENS poderá gerar os tokes a serem utilizados para autenticação das APIs.

<img src="https://content.pstmn.io/eced47c8-a3f7-43c6-a31e-ebeef18fb883/aW1hZ2UucG5n" width="816" height="237">

**IMPORTANTE: Uma vez gerado o TOKEN não será mais exibido na tela em futuras consultas. Deverá armazena-lo em local seguro.Poderá desativar um TOKEN em qualquer momento ou gerar um novo nesse mesma tela.É possivel gerar vários TOKENS para cada aplicação ou server, etc.**2.

**GERAR TOKEN provisório**

Para casos de **uso diretamente em app ou rotinas no cliente final** (JavaScript por ex) é possível utilizar um TOKEN que tem validade de 60 minutos e é gerado pela API GetUserID. No entanto, é recomendado que as autorizações sejam sempre feitas do tipo "server side".

- Gere o token (tsid) na API GetUserID **no seu servidor**. Para gerar nessa API é necessário utilizar um TOKEN PERMANENTE ou autenticação por IP. Uma vez gerado, é valido por 60 minutos no mesmo IP.
- Utilize o token (tsid) nas sua requisições enviando por umas das modalidades:  
    a) Header incluir 'Authorization: Bearer {token}'  
    b) Header incluir 'Authorization: {token}'  
    c) Incluir no JSON "tsid":"{token}"
    

**3\. SERVER IP (ALTERNATIVO)**

**Se utilizar Token, não precisa utilizar essa metodologia.**

Caso tenha um server com IP fixo ou um IP fixo que é mostrado como origem da requisição e é exclusivo, pode programar no painel de controle web em MEUS DADOS-APIs-IPs Autorizados os IPs que serão autorizados a fazer requisições sem as metodologias anteriores.  
**Deve obrigatoriamente enviar um dos usuários da conta no campo user como parâmetro da URL ou parâmetro do JSON.**

<h1>Retorno</h1>

Será retornado o HTTP code e JSON quando o retorno não for uma mídia.

HTTP Codes:

<ul><li><p>200 - OK</p></li><li><p>400 - Parâmetros invadidos ou incompletos</p></li><li><p>401 - Falha na autenticação</p></li></ul>

O retorno em **JSON** contém sempre duas informações básicas e para cada API pode conter outras relativo ao processo solicitado.  
As básicas são:  
**status** é um informe do status ou erro. Se **OK**, a requisição foi aceita e a ligação programada. Se diferente de OK, será informado o texto do erro.

**status_code** é uma identificação numérica do status da solicitação. Quando OK, no status será 0 (zero) e outras conforme tabela a seguir.

| statu | status_code | Details |
| --- | --- | --- |
| OK | 0 | Requisição aceita |
| Session ID is not valid | 100 | Se enviado token tsid e for inválido |
| Session ID is not valid | 100 | Se enviado token tsid e for inválido |
| Session ID expired | 101 | Se enviado token tsid e for expirado |
| IP not authorized | 120 | Se autenticação por IP e o IP for não autorizado |
| Account not exist | 121 | Conta não existente na plataforma |
| Inactive user | 122 | Usuário inativo |
| Non existent user | 123 | Usuário inexistente |
| No user or password | 130 | Usuário ou senha não informados |
| IP trials exceeded | 131 | Tentativas de login erradas excedeu o limite. Bloqueio de 30 min |
| Logins trials exceeded | 132 | Erro de usuário excedeu o limite. Bloqueio de 10 min |
| Username or password invalid | 140 | Usuário ou senha inválido |
| IP blocked | 199 | IP bloqueado |

**Outros status e códigos específicos de cada API estão listados no capítulo de cada uma.**

<h1>APIs e exemplos</h1>

Nesse documento, você poderá verificar detalhes de cada API e **escolher exemplos na linguagem de programação preferida** (escolha no menu superior).  
Também poderá abrir em sua conta **POSTMAN** para fazer testes online.

**APIs mais utilizadas - Individual ou em lote:**

**Individual use: MakeTTSCall ->** Dispara uma ligação individual para um destino ou opcionalmente para dois destinos, unindo as duas ligações.  
Pode ser envio imediato ou com dia e hora programada.

**Em lote use: CreateCampaign ->** Permite a criação de uma campanha para o envio de um lote de destinos (recomendado até 500 mil destinos). Pode ser inteiramente programado pelos parâmetros das APIs ou clonando de uma campanha anterior.

**Nos exemplos a seguir, serão indicadas a autenticação recomendada padrão por TOKEN.**

## End-point: MakeTTSCall
<h4>Descritivo</h4>

API para envio de torpedo de voz para:  
\- Um destino ( com envio opcional de SMS ao final ou quando interagir)  
\- Dois destinos ( atende um destino e faz a ligação para o segundo destino. Aplicaçoes para entregador-cliente, mantendo os números anonimos)  
\- Dois destinos ( liga para cliente e se atender transfere para um call center )

Os atendimentos podem ser áudios fixos, audios com variáveis ou robôs de atendimento com interação por DTMF ou por voz.

Os áudios utilizados na mensagem podem ser gerados por texto ou podem ser áudios pré-gravados, bastando informar o ID do áudio.

<h4>Parâmetros</h4>

- **Parâmetros gerais**
    

**type** = \[tipo de envio, por exemplo, para envio de **um áudio simples type=0**, para **dois destinos type=3**. Para envios interativos por teclado ou por voz, consulte o suporte para outros tipos de envio\]

**dest** = \[Número telefônico do destino no formato DDI+DDD+NÚMERO, exemplo: 5511938421234 \]

**dest2** = \[Número telefônico do segundo destino no formato DDI+DDD+NÚMERO, exemplo: 5511938421234 \]

**setbrasil** = \[1 ou em branco. Se for 1, o sistema assume que são números do Brasil e ajusta para padrão do sistema que usa DDI+DDD+NUMERO. Podendo ser enviado sem o DDI, com o DDD com ou sem o zero que automaticamente o sistema ajusta.\]

**free** = \[OPCIONAL – Se 1 o sistema não irá verificar nas bases do Não Perturbe dos PROCONS. Para BRASIl, utilizar 1 apenas se for para uso em cobrança ou solicitação de envio realizada pelo próprio cliente. DEFAULT=0\]

**bkddd** = \[OPCIONAL – Se 1 (sem registro no CDR) ou 2 (com registro no CDR), o sistema irá verificar se a localidade de destino tem alguma lei ou norma que impeça ligações em determinados dias ou horários. Essa programação é obrigatório para ligações para o BRASIL e se for de conteúdo de telemarketing e cobrança, não sendo necessário ativar quando situaçoes solicitadas pelo clientes, como envios de tokens, click2call, etc. DEFAULT=0=Não ativo\]

**rurl** = \[OPCIONAL: URL com endereço completo com https://...., no qual o sistema irá retornar com um POST ao fim da ligação com os dados da chamada e dados coletados. Caso seja sempre a mesma URL, o melhor é **informar no painel de controle do site em API – URLs de RESPOSTA**\]

**ctid** = \[OPCIONAL: ID fornecido por quem envia para referencia extra ” qualquer valor alfa-numérico até 15 caracteres\]

**priority** = \[OPCIONAL: Padrão = 0 (zero) vai para fila de envios garantido o recebimento da requsição. Se enviar um lote maior e deseja que alguns saiam na frente, alocar um valor maior que zero para os mais prioritários. Se necessita enviar uma ligação de forma imediata para uso em um token ou semelhante solicite o suporte para passar sua conta para envio imediato.**Para envios para dois destinos type=3 , utilize priority=-1** \]

**repeat** = \[OPCIONAL: Parâmetro de repetição ex: 2|30|22:00 (2 tentativas, a cada 30 minutos, até as 22 horas) Se tiver o quarto parâmetro, indica agendamento. Exemplo: 3|30|22:00|2010-04-05 16:00 (1 envio + 2 reenvios se não atender, reenvio a cada 30 minutos, até as 22 horas com a primeira chamada as 16 horas do dia 5 de abril de 2010. Atenção: Ao usar esse parâmetro, o sistema não informa o cd_id pois as ligações serão feitas nos horários programados\].

- **Parâmetros dos áudios**
    

Os áudios utilizados poderão ser gerados por TTS (Text to Speech) ou oriundos de áudios pré gravados por um locutor.

_**Opções recomendadas:**_

1) Áudios que são sempre o mesmo e sem variáveis, tanto produzido por TTS ou por locutor: Criar os áudios na pagina de áudio ou por API, pegar o ID e informa-lo no campo _**content**_

2) Áudios com **uma única variavel**: Criar os áudios na pagina de áudio ou por API, pegar o ID, informa-lo no campo **content e a variavel utilizada (nome, cod_cli, extra1, extra2 e extra3)**

3) Áudios com várias variáveis ou que se alterem constantemente e que são gerado por TTS : Informar o texto já com as variaveis substituidas no campo _**text**_

4) Áudio oriundos de locutor com variáveis : Criar os áudios na pagina de áudio ou por API, pegar o ID, informa-lo no campo **content e adicionamente informar as variáveis opcionais nome, cod_cli, extra1, extra2 e extra3.** Nesse caso cada parte do audio do locutor deve ser criado um áudio separado e depois na criação do audio modelo, que será informado no **content**, interliga-lo com os nomes das variáveis.

Obs: Os áudios que serão informados nos parâmetros ‘contents’ e seus códigos são obtidos no painel de controle web, no momento da geração dos áudios ou na listagem dos áudios e também podem ser enviados ou gerados na plataforma pela API CreateAudioFile.

Dependendo do tipo de mensagem poderão ser utilizados:**content** = \[Código do Áudio que iniciará a mensagem – obrigatório mesmo se for um áudio mudo com uma pequena pausa\]

**No caso de envio simples, de um áudio fixo, apenas será utilizado o content. Outros tipos de envio podem usar:**

**content1** = \[Código do Áudio que encerra caso o destino responda que não deseja informar\]

**content2** = \[Código do Áudio da pergunta após confirmação que deseja informar\]

**content3** = \[Código do Áudio que finaliza a mensagem após a coleta do dado\]

**contentno** = \[Código do Áudio caso não seja digitado o dado\]

**contentfail** = \[Código do Áudio caso falhe a ligação para o segundo destino\]  

- **Usando o TTS:** Caso seja necessária a geração de áudio especifico para cada envio, basta utilizar o parâmetro **text** com o texto do áudio. O parâmetro text tem prioridade sobre o parâmetro content, assim mesmo tendo os 2 parâmetros na mesma requisição, o text é que será utilizado.
    

**voice** = \[Opcional – se “fad” é voz feminina . Se “fel” é voz masculina. Em branco ou não enviado assume fad. Ver tabela completa em CreateAudioFile\]

**text** = \[Obrigatório se não estiver informando o **content**\- Texto do Áudio correspondente ao ‘content’\]

**text1** = \[Opcional - Texto do correspondente ao ‘content1’\]

**text2** = \[Opcional - Texto do correspondente ao ‘content2’\]

**text3** = \[Opcional - Texto do correspondente ao ‘content3’\]

**encoding** = \[Opcional: UTF-8 / ASCII / ISO-8859-1 – Se não enviado assume que o texto é no padrão UTF-8. Se utilizar JSON para encaminhar, é obrigatório UTF-8.  
Algumas funções como Curl normalmente convertem para utf-8 automaticamente, assim se converter palavras do pt-BR para UTF-8 e depois enviar para o Curl pode gerar erros. Se já estiver em ISO-8892, prefira enviar em ISO-8892 e deixar o Curl converter.\]

**UMA variável : Usando TTS com uma variável**: Para envios múltiplos **em que apenas uma variável é substituída**, como por exemplo um nome que se altera em cada mensagem, use a seguinte metodologia:

a) Crie um áudio pelo site ou pela API CreateAudioFile que contenha uma das seguintes variáveis: NOME, COD_CLI, EXTRA1 ou EXTRA2. (em letras maiúsculas)

“Olá NOME, temos uma mensagem importante para você. Caso deseje ouvir, digíte 1...”

b) No parâmetro content a ser utilizado, use o ID do áudio modelo criado. Não informe nada nos parâmetros texts, deixe-os em branco.

c) Enviar para cada disparo no parâmetro “nome”, “cod_cli”, “extra1” ou “extra2” o dado correspondente ao áudio.

**nome** = \[Opcional – Variável que será substituída ao encontrar NOME no modelo de áudio informado nos “contents”\]

**cod_cli** = \[Opcional – Variável que será substituída ao encontrar COD_CLI no modelo de áudio informado nos “contents”\]

**extra1** = \[Opcional – Variável que será substituída ao encontrar EXTRA1 no modelo de áudio informado nos “contents”\]

**extra2** = \[Opcional – Variável que será substituída ao encontrar EXTRA2 no modelo de áudio informado nos “contents”\]

**extra3** = \[Opcional – Variável que será substituída ao encontrar EXTRA3 no modelo de áudio informado nos “contents”\]

- **Outros parâmetros do MakeTTSCall**
    

**Para envios interativos por teclado ou por voz, consulte o suporte**

**dtmf** = \[parâmetro para campanhas interativas\]

**dtmf2** = \[parâmetro para campanhas interativas\]

**nans** = \[parâmetro para campanhas interativas\]

**ndig** = \[parâmetro para campanhas interativas\]

- _**Parâmetros para envio de SMS ao final da ligação**_
    

**É possivel** enviar um SMS automáticamente para o destinopara ligações atendidas, não atendidas, ambas ou quano o destino teclou uma tecla determinada.

**sms_text** = \[Opcional – Texto de até 160 caracters para envio de SMS ao final da ligação \]

**sms_action** = \[Opcional – Ativa envio de SMS após desligamento – ok nae oknae dtmf1 \]

**sms_dtmf** = \[Opcional – Teclas que acionam o envio do SMS quando a opção do **sms_action for dtmf1** - teclas separadas por vírgula ou espaço. Ex: 1,2,3 - SMS será enviado se teclou 1, 2 ou 3 - Default = 1 \]

| **sms_action** | **descritivo** |
| --- | --- |
| ok | Envia SMS para os destinos que atenderam |
| nae | Envia SMS para os que não atenderam |
| oknae | Envia SMS para os que atenderam e não atenderam |
| dtmf1 | Envia SMS para aquelas que teclaram |

<h2>Retorno</h2>

**cd_id** é uma identificação alfa numérica única correspondente ao envio. Lembramos que se pode enviar junto da requisição o ctid, uma identificação única da plataforma que requisitou e essa identificação será retornada. Atenção: se utilizado parâmetro repeat, o valor do cd_id não será informado, sendo recomendável utilizar o ctid para retorno e rastreamento.

**Sempre que o status vier diferente de OK (ou status_code diferente de zero), a ligação não será realizada.**

| status | status_code | Details |
| --- | --- | --- |
| OK | 0 | Áudios gerados e requisição do envio aceita |
| urlcontent invalida | 202 | Se enviado áudio por URL e for inválido |
| number invalid | 203 | Número incorreto |
| block ddd time | 230 | Número bloqueado por lei ou norma devido ao horário ou dia |
| error sent message no destination | 250 | Sem número do destino |
| error sent message error destination | 250 | Quantidade de dígitos do destino incompatível |
| error sent message no content | 250 | Sem informações sobre o áudio a ser reproduzido |
| error sent message CA | 250 | Bloqueio de ligação por ultrapassar o limite de envios permitidos para o mesmo numero. Só ativo e possível se fornecido o parâmetro de limitação “numlim” |
| error sent message BK_PROCON | 250 | Número bloqueado no PROCON. Lista de não perturbe. |
| error sent message Blocked | 250 | Número que está na lista de bloqueados informado pelo cliente. Só verifica se estiver passando também pela verificação do PROCON |
| error sent message No credit ID | 250 |  |
| error audio file | 260 | Se ultrapassar o limite de crédito disponível para a conta |
| Sms only in type 0 | 300 | SMS apenas no tipo áudio único |
| Sms no action | 301 | Envio de SMS necessita parâmetro sms_action |
| Sms no text | 302 | Envio de SMS necessita parâmetro sms_text |
| Invalid sms_action | 304 | sms_action inválido |
| Sms text 160 characters | 305 | Texto de SMS com mais de 160 caractéres |

## Códigos e exemplos
### Method: POST
>```
>/api/v2/MakeTTSCall
>```
### Headers

|Content-Type|Value|
|---|---|
|Content-Type|application/json|


### Headers

|Content-Type|Value|
|---|---|
|Authorization|Bearer |


### Body (**raw**)

```json
{"type":"0","content":"tf185409063","priority":"0","free":"1","dest":"5519992069730","nome":"José Roberto"}
```

### 🔑 Authentication noauth

|Param|value|Type|
|---|---|---|


### Response: undefined
```json
{
    "return": {
        "status": "OK",
        "status_code": "0",
        "cd_id": "c_88700"
    }
}
```


⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃

## End-point: CreateCampaign
<h2>Descritivo</h2>

A API CreateCampaign cria campanhas para envio em lote. Essas campanhas também podem ser programadas pelo painel de controle [https://velip.com.br](https://velip.com.br)

Os destinos podem ser informados:

*   Por JSON, no corpo da requisição
*   Por arquivo contendo o JSON
*   Por arquivo em CSV  
    O número máximo recomendados para envio em lote (campanha) é de 500.000 destinos.
    

Criar campanhas:

*   Tipo “Simples”, áudio único com ou sem TTS de variáveis (NOME/COD_CLI/EXTRA1/EXTRA2)
*   Tipo “Pergunta mais validação de dado”
*   Clonar - Qualquer tipo campanha baseada em outra campanha existente (ID da campanha a ser clonada) inclusive campanhas de VOICEBOT.
    

<h2>Parâmetros</h2>

*   **Parâmetros comuns a qualquer tipo:**
    

**date_start** = \[data inicial formato YYYY-mm-dd\]

**date_end** = \[data final formato YYYY-mm-dd\]

**time_start** = \[hora inicial format HH:MM:SS\]

**time_end** = \[hora final format HH:MM:SS\]

*   **Parâmetros para a base de destinos (telefone, nome, cpf, etc):**
    

Utilize uma das três possibilidades de enviar os destinos.

**cdlc_id** = \[ID da lista de destinos\] Criada pelo painel de controle ou pela API CreateDestinationBase

ou

**datajson** = \[Dados em JSON com os destinos\] Ver detalhes do padrão JSON na API CreateDestinationBase

ou

**Por Upload de arquivo** Se escolhido esse método o arquivo deverá ser enviados por UPLOAD (multipart/form-data).  
O **nome do arquivo dever ser com o sufixo ( CSV,JSON,TXT).

Se fosse um form html seria:

*   **Parâmetros para campanha tipo áudio único:**
    

O tipo simples é uma ligação que ao atender reproduz um áudio, fixo ou com as variáveis (NOME/COD_CLI/EXTRA1/EXTRA2/EXTRA3).

**content** = \[ID do áudio (cdw_file)\]  
ou  
**text** = \[Texto do áudio a ser reproduzido\]  
**voice** = **voice** = \[Opcional – Voz utilizada no TTS - Se “fad” é voz feminina e se “fel” é voz masculina. Em branco ou não enviado, assume fad. Ver tabela completa em CreateAudioFile\]

*   **Parâmetros para tipo CLONAGEM DE CAMPANHA:**
    

Essa opção é útil para fazer o mesmo tipo de campanha rotineiramente, bem como gerar campanhas de outros tipos apenas disponíveis pelo painel de controle. Com essa API, qualquer campanha/tipo gerada pelo painel pode ser gerada por API. Note que a base de destino e datas precisam ser informados a cada vez que a campanha for gerada. O horário, se não informado, assume da campanha a ser clonada e a data da requisição.

**cp_id** = \[ID da campanha que será clonada\] Esse Id pode ser verificado na listagem de campanhas no painel de controle.

*   **Parâmetros opcionais para qualquer tipo de envio em lote (campanha):**
    

**name** = \[Opcional – nome da campanha – se em branco, assume nome da base de destinos – max. 50 caracteres\]

**detail** =\[Opcional – descritivo da campanha – max. 256 caracteres\]

**group** = \[Opcional – ID do grupo\]

**amd** = \[Opcional – ID do áudio que é reproduzido se detectar sec. eletrônica – ativa detector de sec. eletrônica\]

**max_answered** = \[Opcional – limite de ligações atendidas – Default = sem limite \]

**mobile** = \[Opcional – permite envio para celular – 1 sim e 0 não – Default = 1 \]

**vel** = \[Opcional – velocidade de envios por minuto – permitido de 1 a 100 ou max - Default = max\]

**resends** = \[Opcional – número de reenvios as não atendidas – de 1 a 3 – Default = 1 \]

**time_resends** = \[Opcional – intervalo entre os reenvios – de 10 a 240 min – Default = 30 \]

**no_block** = \[Opcional – busca bloqueio PROCON – 1 não verifica no PROCON e 0 verifica – Default = 0 \]

**limit_name** = \[Opcional – limita número de nomes quando TTS do NOME – 1 um nome, 2 Nome e Sobre , 3 todos – Default =1\]

*   ***Parâmetros opcionais para envio de SMS no tipo áudio único:***
    

**É possivel, no tipo de campanha um áudio único**, enviar um SMS automáticamente para o destino. Para os demais tipos de campanhas, o envio de SMS pode ser feito utilizando a API MakeSMS após receber o callback do resultado da ligação.

**sms_text** = \[Opcional – texto de até 160 caracters para envio de SMS ao final da ligação\]

**sms_action** = \[Opcional – ativa envio de SMS após desligamento – ok nae oknae dtmf1\]

| **sms_action** | **descritivo** |
| --- | --- |
| ok | Envia SMS para os destinos que atenderam |
| nae | Envia SMS para os que não atenderam |
| oknae | Envia SMS para os que atenderam e não atenderam |
| dtmf1 | Envia SMS para aquelas que teclaram 1 |

<h2>Retorno</h2>

**cp_id** é uma identificação alfa numérica única correspondente ao ID da campanha gerada.

**Sempre que o status vier diferente de OK (ou status_code diferente de zero) a campanha não foi programada.**

| statu | status_code | Details |
| --- | --- | --- |
| OK | 0 | Campanha programada |
| FTP programming does not exist | 200 | Programa FTP para relatório não válido |
| not allowed executable file | 205 | Upload de arquivo não aceitável |
| limits answered calls invalid | 212 | Limite de ligações atendidas inválido |
| allow mobile - invalid | 213 | Permite mobile inválido |
| Invalid speed limit | 214 | Limite de velocidade inválido |
| Invalid number of resends | 215 | Número de reenvios inválido |
| Invalid interval between resends | 216 | Intervalo entre reenvios inválido |
| cd_type invalid | 217 | Tipo de campanha inválida |
| Invalid - disables PROCON | 218 | Desativa PROCON inválido |
| Invalid DTMF filter | 219 | Filtro de DTMF inválido |
| Invalid date start | 220 | Data inicial inválida |
| Invalid date start | 221 | Data final inválida |
| Invalid time start | 222 | Hora inicial inválida |
| Invalid time start | 223 | Hora final inválida |
| Campaign insertion error | 225 | Erro na inserção da campanha |
| Invalid limit name | 227 | Limita nome inválido |
| Active campaign with same date | 230 | Outra campanha ativa com mesma data |
| Initial audio not found | 240 | Áudio inicial não localizado |
| AMD audio not found | 241 | Áudio AMD não localizado |
| Audio not found | 242 | Áudio não localizado |
| contentno audio not found | 243 | Áudio AMD não localizado |
| contentfail audio not found | 244 | Áudio AMD não localizado |
| Group not found | 250 | Grupo não localizado |
| Invalid base ID | 251 | Base de destinos inválida |
| Invalid compw | 252 | compw inválido |
| Error inserting model | 260 | Erro na inserção do modelo |
| Campaign insertion error | 261 | Erro na inserção da campanha |
| Error in parameters | 262 | "Erro nos parâmetros da campanha |
| Base generation error | 270 | Erro na geração da base de destinos |
| Error in audio generation | 281 | Erro na geração de áudio |
| Invalid number of responses | 290 | Numero de respostas inválido |
| Invalid response time | 291 | Tempo de resposta inválido |
| Sms only in type 0 | 300 | SMS apenas no tipo áudio único |
| Sms no action | 301 | Envio de SMS necessita parâmetro sms_action |
| Sms no text | 302 | Envio de SMS necessita parâmetro sms_text |
| Invalid sms_action | 304 | sms_action inválido |
| Sms text 160 characters | 305 | Texto de SMS com mais de 160 caractéres |

<h2>Códigos e exemplos</h2>
### Method: POST
>```
>https://vox.velip.com.br/api/v2/CreateCampaign
>```
### Headers

|Content-Type|Value|
|---|---|
|Content-Type|application/json|


### Headers

|Content-Type|Value|
|---|---|
|Authorization|Bearer |


### Body (**raw**)

```json
{"cp_id":"210551","date_start":"2021-02-23","date_end":"2021-02-24","time_start":"09:00:00","time_end":"10:00:00","cdlc_id":"229186"}
```

### 🔑 Authentication noauth

|Param|value|Type|
|---|---|---|


### Response: 201
```json
{
    "return": {
        "status": "OK",
        "status_code": "0",
        "cp_id": "210576"
    }
}
```


⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃

## End-point: ChangeCampaign
<h2>Descritivo</h2>

A API ChangeCampaign edita os parâmetros de campanhas (envios em lote) já geradas. Também pode ser utilizada para ver o status de uma campanha.

<h2>Parâmetros</h2>

**cp_id** = \[Obrigatório - ID da campanha – Se outros parâmetros não forem fornecidos serve para ver dados da campanha\]

Parâmetros que podem ser alterados de uma campanha:  
(Só é necessário informar aqueles que deseja alterar.)

**cp_active** = \[0 para inativa ou 1 para ativa\] Obs: nesse caso o melhor seria um check para a pessoa inativar ou ativar.  
  
**cp_date_start** = \[data inicial ( YYYY:MM:DD)\]  
  
**cp_date_end** = \[data final ( YYYY:MM:DD)\]  
  
**cp_time_start** = \[hora inicial (HH:MM:SS ou HH:MM )\] 0bs: melhor mostrar e editar apenas HH:MM  
  
**cp_time_end** = \[hora final (HH:MM:SS ou HH:MM )\] 0bs: melhor mostrar e editar apenas HH:MM  
  
**cp_lig_min** = \[Envios por minuto sendo “max” para o máximo possível ou valor numérico.\] No site fixei um drop-down em max,5,10,20, 50,100 que pode ser o mesmo no app.  
  
**cp_pas** = \[Posições de atendimento(PAs) para campanhas com transferência.\] Esse valor só dever ser mostrado e editado se não vier “null” . Quando vem “null” significa que a campanha não é de PA virtual (transferência)  

<h2>Retorno</h2>

**cp_id**: ID da campanha  
  
**cp_name**: Nome da campanha  
  
**cp_group**: nome do grupo da campanha  
  
**cp_active**: 0 para inativa e 1 para ativa  
  
**cp_ctid**: Customer ID da campanha  
  
**cp_ontime**: 0 para fora do horário programado e 1 para dentro do horário programado  
  
**cp_date_start**: data inicial programada  
  
**cp_date_end**: data final programada  
  
**cp_time_start**: hora inicial programada  
  
**cp_time_end**: hora final programada  
  
**cp_destinations**: número de destinos  
  
**cp_lig_min**: número de ligações por minuto programado  
  
**cp_pas**: número de PAs programadas para atendimento para tipo com transferência  
  
**cp_made**: ligações realizados  
  
**cp_answered**: ligações atendidas  
  
**cp_transfered**: ligações transferidas para call center (campanhas de atendente virtual)  
  
**cp_madel**: 1 sim 0 não - se for modelo

<h2>Códigos e exemplos</h2>
### Method: POST
>```
>https://vox.velip.com.br/api/v2/ChangeCampaign
>```
### Headers

|Content-Type|Value|
|---|---|
|Content-Type|application/json|


### Headers

|Content-Type|Value|
|---|---|
|Authorization|Bearer |


### Body (**raw**)

```json
{"cp_id":"210551","date_start":"2021-02-23","date_end":"2021-02-24","time_start":"09:00:00","time_end":"10:00:00","cdlc_id":"229186"}
```

### 🔑 Authentication noauth

|Param|value|Type|
|---|---|---|


### Response: 201
```json
{
    "return": {
        "status": "OK",
        "status_code": "0",
        "cp_id": "210576"
    }
}
```


⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃

## End-point: GetCampaignsList
<h2>Descritivo</h2>

A API GetCampaignsList retorna uma listagem das campanhas com dados resumo ontime.

<h2>Parâmetros</h2>

**maxreg** = \[Opcional - número de registros retornados. Se não informado limita em 100. Para sem limites colocar 0 (zero)\]  
  
**cp_id** = \[Opcional – ID de uma campanha gerado pela plataforma\]  
  
**cp_ctid** = \[Opcional – ID da campanha informado pelo cliente ao gerar uma campanha por API\]  
  
**group** = \[Opcional – ID do Grupo\]  
  
**date** = \[Opcional – Campanhas de uma data\]  
  
**search** = \[Opcional – Busca no nome e descritivo\]  
  
**model** = \[Opcional – 1 para modelos, 0 para todas\]  

<h2>Retorno</h2>

**cp_id**: ID da campanha  
  
**cp_name**: Nome da campanha  
  
**cp_ctid**: Customer ID da campanha  
  
**cp_group**: nome do grupo da campanha  
  
**cp_active**: 0 para inativa e 1 para ativa  
  
**cp_ontime**: 0 para fora do horário programado e 1 para dentro do horário programado  
  
**cp_date_start**: data inicial programada  
  
**cp_date_end**: data final programada  
  
**cp_time_start**: hora inicial programada  
  
**cp_time_end**: hora final programada  
  
**cp_destinations**: número de destinos  
  
**cp_lig_min**: número de ligações por minuto programado  
  
**cp_pas**: número de PAs programadas para atendimento para tipo com transferência  
  
**cp_made**: ligações realizados  
  
**cp_answered**: ligações atendidas  
  
**cp_transfered**: ligações transferidas para call center ( campanhas de atendente virtual)  
  
**cp_madel**: 1 sim 0 não - se for modelo

<h2>Códigos e exemplos</h2>
### Method: POST
>```
>https://vox.velip.com.br/api/v2/GetCampaignsList
>```
### Headers

|Content-Type|Value|
|---|---|
|Content-Type|application/json|


### Headers

|Content-Type|Value|
|---|---|
|Authorization|Bearer |


### Body (**raw**)

```json
{"maxreg": "10","search":"teste"}
```

### 🔑 Authentication noauth

|Param|value|Type|
|---|---|---|


### Response: 201
```json
{
    "return": {
        "status": "OK",
        "status_code": "0"
    },
    "campaigns": [
        {
            "cp_id": "210580",
            "cp_name": "API_json_2_2021_02_26_15_45_10",
            "cp_ctid": "null",
            "cp_group ": "null",
            "cp_active ": "1",
            "cp_ontime ": "0",
            "cp_date_start": "2021-02-23",
            "cp_date_end": "2021-02-24",
            "cp_time_start": "09:00",
            "cp_time_end": "10:00",
            "cp_destinations": "3",
            "cp_lig_min": "max",
            "cp_pas": "null",
            "cp_made": "0",
            "cp_answered": "0",
            "cp_transfered": "null",
            "cp_model": "0"
        },
        {
            "cp_id": "210579",
            "cp_name": "Teste JRA EXTRA1 a 4",
            "cp_ctid": "null",
            "cp_group ": "null",
            "cp_active ": "1",
            "cp_ontime ": "0",
            "cp_date_start": "2021-02-23",
            "cp_date_end": "2021-02-24",
            "cp_time_start": "09:00",
            "cp_time_end": "10:00",
            "cp_destinations": "1",
            "cp_lig_min": "max",
            "cp_pas": "null",
            "cp_made": "0",
            "cp_answered": "0",
            "cp_transfered": "null",
            "cp_model": "0"
        },
        {
            "cp_id": "210578",
            "cp_name": "API_json_2_2021_02_26_15_38_30",
            "cp_ctid": "null",
            "cp_group ": "null",
            "cp_active ": "1",
            "cp_ontime ": "0",
            "cp_date_start": "2021-02-23",
            "cp_date_end": "2021-02-24",
            "cp_time_start": "09:00",
            "cp_time_end": "10:00",
            "cp_destinations": "3",
            "cp_lig_min": "max",
            "cp_pas": "null",
            "cp_made": "0",
            "cp_answered": "0",
            "cp_transfered": "null",
            "cp_model": "0"
        }
    ]
}
```


⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃

## End-point: CreateAudioFile
<h2>Descritivo</h2>

A API CreateAudioFile é para criar por TTS ou enviar por upload áudios a serem utilizados em qualquer serviço nosso, como torpedo de voz, robôs de atendimento, call center em nuvem e humanos digitais.  
Por exemplo, se tiver um envio em lote e tem um áudio de um locutor pode enviar esse áudio pela CreateAudioFile e na CreateCampaing usando o ID desse áudio.

**O upload de áudio ou a geração de áudio por texto (TTS) também podem ser processadas, sem nenhuma integração, diretamente no painel de controle.**

<h2>Parâmetros</h2>

*   **Parâmetros gerais para TTS e UPLOAD:**
    

**name** = \[Opcional: apelido do áudio que irá aparecer na listagem com até 50 caracteres. Não necessariamente o nome do arquivo\]  
  
**expires** = \[data no formato YYYY:MM:DD No inicio de cada dia serão apagados os áudios de datas inferiores\]  
  
Se não informado o sistema assume 3 meses a partir da data da criação.  
Quando se esta gerando áudios para testes via um texto (TTS) esse parâmetro não tem valor. Quando deseja aceitar o texto/audio (ttswrt=1) o valor de “expires” pode ser informado conforme sua previsão do tempo de uso ou assumirá os 3 meses do padrão.  
  
**mp3** = \[Opcional: se não for utilizar o mp3 gerado para ouvir o áudio utilize mp3=NO e a velocidade de geração irá aumentar\]  
  
**ttswrt** = \[Depois de testar e verificar se ficou bom o áudio, é necessário gerar novamente com esse parâmetro igual a 1. Se gerar com ttswrt em branco ou diferente de 1, o áudio será apenas para audição de teste e não poderá ser utilizado nos serviços\]

*   **Parâmetros para TTS**
    

**text** = \[texto do áudio com charset = utf-8\]  
**encoding** = \[Opcional : UTF-8 / ASCII / ISO-8859-1 – Se não enviado, assume que o texto é no padrão UTF-8. Se utilizar JSON para encaminhar, é obrigatório UTF-8. Algumas funções como Curl normalmente convertem para utf-8 automaticamente, assim, se converter palavras do pt-BR para UTF-8 e depois enviar para o Curl poderá gerar erros. Se já estiver em ISO-8892, prefira enviar em ISO-8892 e deixar o Curl converter.\]  
  
**voice** = \[Opcional – Abaixo uma tabela com as vozes\]

*   **Parâmetros para UPLOAD**
    

**audio64** = \[arquivo de áudio no formato audio64 enviado no JSON ou no parâmetro do POST\]  
  
**ou**  
  
**audio** = \[arquivo de áudio enviados por UPLOAD (multipart/form-data)\]  
  
Se escolhido esse método o arquivo deve ser enviados por UPLOAD (multipart/form-data).  
  
Se fosse um form html seria:  

  
  
  
  
  
  

<h2>Retorno</h2>

**cdw_file**: ID do áudio  
  
**cdw_file_test**: ID do áudio quando ttswrt for diferente de 1. Para ouvir se o TTS está correto por ex.  
  
**cdw_name**: Nome do áudio  
  
**cdw_sec**: Duração em segundos do áudio  
  
**cdw_expires**: Data de expiração do áudio  
  
**cdw_type**: Tipo de geração, tts ou upload.

<h2>Códigos e exemplos</h2>
### Method: POST
>```
>https://vox.velip.com.br/api/v2/CreateAudioFile
>```
### Headers

|Content-Type|Value|
|---|---|
|Content-Type|application/json|


### Headers

|Content-Type|Value|
|---|---|
|Authorization|Bearer |


### Body (**raw**)

```json
{"text":"Esté é um teste de geração de áudio","ttswrt":"1","voice":"MS|pt-BR-FranciscaNeural","name":"Teste de Áudio", "encoding":""}
```

### 🔑 Authentication noauth

|Param|value|Type|
|---|---|---|


### Response: 201
```json
{
    "return": {
        "status": "OK",
        "status_code": "0",
        "cdw_file": "tf187533254",
        "cdw_file_test": "tf187533254",
        "cdw_name": "teste de áudio",
        "cdw_sec ": "3.0",
        "cdw_expires ": "2026-02-28",
        "cdw_type ": "tts"
    }
}
```


⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃

## End-point: PlayAudioFile
<h2>Descritivo</h2>

A API PlayAudioFile retorna um áudio para reprodução ou arquivo. Pode ser usado como uma URL de um áudio.  
Retorna no formato mp3

<h2>Parâmetros</h2>

**cdw_file** = \[ID do áudio a ser retornado\]  
  
ou  
  
**cdw_file_test** = \[ID do áudio de teste gerado pelo CreateAudioFile para verificação se está correto o TTS\]  

**noheader** = \[Opcional – yes para não enviar headers no retorno\]  

Obs.: se necessitar usar como uma URL para algum player diretamente, sem passar por um server intermediário, deve usar em conjunção cpm GetUserID para gerar um token(tsid) e esse token ser enviado nos parâmetros da URL em conjunto com o cdw_file.  
  
Ex: [https://vox.velip.com.br/api/v2/CreateAudioFile?tsid=123abcd456&cdw_file=tf123456](https://vox.velip.com.br/api/v2/CreateAudioFile?tsid=123abcd456&cdw_file=tf123456)

<h2>Retorno</h2>

**Retorno o áudio em mp3**  
  
Com Header:  
  
"Content-Type: audio/mpeg"

Se algum erro -> HTTP status: 401 e JSON com status e status_cod

<h2>Códigos e exemplos</h2>
### Method: POST
>```
>https://vox.velip.com.br/api/v2/PlayAudioFile?tsid&cdw_file=tf187515162
>```
### Headers

|Content-Type|Value|
|---|---|
|Content-Type|application/json|


### Headers

|Content-Type|Value|
|---|---|
|Authorization|Bearer |


### Body (**raw**)

```json

```

### Query Params

|Param|value|
|---|---|
|tsid|null|
|cdw_file|tf187515162|


### 🔑 Authentication noauth

|Param|value|Type|
|---|---|---|



⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃

## End-point: GetAudiosList
<h2>Descritivo</h2>

A API GetAudiosList retorna uma listagem dos áudios disponíveis na plataforma.

<h2>Parâmetros</h2>

**maxreg** = \[Opcional - número de registros retornados. Se não informado limita em 100. Para sem limites colocar 0 (zero)\]  
  
**type** = \[Opcional – Se desejar filtrar por tts/uplaod/rec\]  
  
**search** = \[Opcional – Busca no nome ou pelo ID do áudio\]

<h2>Retorno</h2>

**cdw_file**: ID do áudio  
  
**cdw_name**: Nome do áudio  
  
**cdw_sec**: Duração em segundos do áudio  
  
**cdw_date**: Data de criação do áudio  
  
**cdw_expires**: Data de expiração do áudio  
  
**cdw_type**: Tipo de geração, tts/upload/rec.

<h2>Códigos e exemplos</h2>
### Method: POST
>```
>https://vox.velip.com.br/api/v2/GetAudiosList
>```
### Headers

|Content-Type|Value|
|---|---|
|Content-Type|application/json|


### Headers

|Content-Type|Value|
|---|---|
|Authorization|Bearer |


### Body (**raw**)

```json

```

### 🔑 Authentication noauth

|Param|value|Type|
|---|---|---|



⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃

## End-point: CreateDestinationBase
<h2>Descritivo</h2>

A API CreateDestinationBase cria uma base de destinos para envio em lote. Essa função também pode ser realizada pelo painel de controle [https://velip.com.br](https://velip.com.br).  
  
A API de geração de campanha em lote CreateCampaign também pode gerar a base de destino simultaneamente com a programação da campanha.  
  
A finalidade dessa API CreateDestinationBase é quando necessita gerar em processos separados a base de destinos para uso posterior por exemplo.

Os destinos podem ser informados:

*   por JSON, no corpo da requisição
*   por arquivo contendo o JSON
*   por arquivo em CSV  
      
    O número máximo recomendados para envio em lote(campanha) é de 500.000 destinos.
    

<h2>Parâmetros</h2>

*   **Parâmetros comuns a qualquer modalidade de envio da base:**
    

**name** = \[opcional- Apelido que irá ser mostrado nas listagens\]  
  
**ctid** = \[opcional - ID único do cliente para identificação própria\]

*   **Parãmetros para a base de destinos (telefone, nome, cpf, etc):**
    

Utilize uma das possibilidades para encaminhar os destinos.

**datajson** = \[Dados em JSON com os destinos\]  
  
ou  
  
**Por Upload de arquivo.** Se escolhido esse método, o arquivo deverá ser enviados por UPLOAD (multipart/form-data).  
O **nome do arquivo dever ser com o sufixo (CSV,JSON,TXT).  
  
  
Se fosse um form html seria:  

  
  
  
  
  
  

*   **Detalhes do JSON de destinos:**
    

Para cada destino é possível informar os seguintes dados:  

**NUMERO, NOME, CODCLI, EXTRA1, EXTRA2 e EXTRA3**  
  
Esses dados servem para disparar a ligação para o NUMERO bem como identificar o destino através de um ou mais Ids, como o CPF que normalmente é informado no CODCLI.  
Além de servir para identificação nos relatórios ou callbacks, esses dados de cada destino podem ser utilizados para personalizar um áudio com TTS, por exemplo:  
  
**Olá NOME informamos que consta um débito do valor de EXTRA1 no seu cartão.**  

O **dado obrigatório é o NUMERO** os outros são opcionais.  

**Existem 2 formatos de JSON (UTF-8) possíveis:**  

1) JSON com nomes de cada variável (pair-value) conforme exemplo:  

\[ {"number":"11 98774-1414","name":"Jose Pedro","codcli":"4544568","extra1":"R$30,00","extra2":"40","extra3":"cartao" },{"number":"21 97654-1414","name":"Maria Roberta","codcli":"4555569","extra1":"R$39,00","extra2":"58","extra3":"credito" }\]  

ou  

2) JSON sequencial. Note que é um array sequencial, a identificação é dada pela posição no array:  

Array base: \[ "NUM_DO DESTINO" , "NOME" , "CODCLI" , "EXTRA1" , "EXTRA2" , "EXTRA3" \]

União de destinos:

\[  
  
\[ "NUM_DO DESTINO" , "NOME" , "CODCLI" , "EXTRA1" , "EXTRA2" , "EXTRA3" \] ,  
\[ "NUM_DO DESTINO2" , "NOME2" , "CODCLI2" , "EXTRA1_2" , "EXTRA2_2" , "EXTRA3_2" \] ,  
\[ "NUM_DO DESTINO3" , "NOME3" , "CODCLI3" , "EXTRA1_3" , "EXTRA2_3" , "EXTRA3_3" \] ,  
\[... até o final dos destinos \]  
\]  

*   Exemplo para 3 destinos com todos os campos:  
    \[ \["11 98442-1414","Jose Roberto","4544568","R$30,00","40","cartao" \] , \[ "19 96539-2325","Pedro Antonio","8542875","R$45,00","20","debito" \] , \[ "11 3245-2020","Maria Jose ","3256485","R$76,00","60","carne" \] \]  
    Exemplo caso não utilize os campos opcionais – Apenas NUMERO:  
    \[ "11 98442-1414" , "19 96539-2325" , "11 3245-2020" \]  
    
*   Exemplo para 3 destinos apenas com NUMERO:  
    

\[ \["11 98442-1414" \] , \[ "19 96539-2325" \] , \[ "11 3245-2020"\] \]  

*   Exemplo para 3 destinos com NUMERO e EXTRA3:  
      
    Se utilizar parcialmente os campos, o JSON deve conter todas as opções, deixando em branco as que não utilizar:  
    
    \[ \["11 98442-1414","","","","","cartao" \] , \[ "19 96539-2325","","","","","debito" \], \["11 3245-2020","","","","","carne" \] \]  
    

<h2>Retorno</h2>

**cdlc_id**: ID da base de destinos  
  
**num_dest**: Número de destinos da base  
  
**base_size**: Tamanho do arquivo quando enviado por upload  

**Sempre que o status vier diferente de OK (ou status_code diferente de zero), a base não foi gerada.**

| statu | status_code | Details |
| --- | --- | --- |
| OK | 0 | Campanha programada |
| not allowed executable file | 205 | Arquivo enviado por upload inválido |
| Error BASE + Detail of error | 230 | Upload de arquivo não aceitável |

<h2>Códigos e exemplos</h2>
### Method: POST
>```
>https://vox.velip.com.br/api/v2/CreateDestinationBase
>```
### Headers

|Content-Type|Value|
|---|---|
|Content-Type|application/json|


### Headers

|Content-Type|Value|
|---|---|
|Authorization|Bearer |


### Body (**raw**)

```json
{"name":"210551","ctid":"123456","datajson":[ ["11 98442-1414","José Roberto","4544568","R$30,00","40","cartao" ] , [ "19 96539-2325","Pedro Antônio","8542875","R$45,00","20","débito" ] , [ "11 3245-2020","Maria José ","3256485","R$76,00","60","carnê" ] ]}
```

### Query Params

|Param|value|
|---|---|
|name|Teste de up base ação|
|ctid|123456|


### 🔑 Authentication noauth

|Param|value|Type|
|---|---|---|


### Response: 201
```json
{
    "return": {
        "status": "OK",
        "status_code": "0",
        "cp_id": "210577"
    }
}
```


⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃

## End-point: GetDestinationsList
<h2>Descritivo</h2>

A API GetDestinationList retorna uma listagem dos bases de destino disponíveis na plataforma ou uma especificamente.

<h2>Parâmetros</h2>

**maxreg** = \[Opcional - número de registros retornados. Se não informado limita em 100. Para sem limites colocar 0 (zero)\]  
  
**search** = \[Opcional – Busca no nome ou pelo ID do áudio\]  
  
**list** = \[Opcional – Se 0(zero) busca apenas bases inativas, se 1(hum) apenas as ativas e se "all" todas - Default=1\]  
  
**cdlc_id** = \[Opcional – Busca pelo ID da base\]  
  
**ctid** = \[Opcional – Busca pelo ID único do cliente previamente informado quando da requisição\]  
  
**setactive** = \[Opcional – Seta base como ativa ou inativa. Se "1", ativa e se "0", inativa - Default: mantém base inalterada\]

<h2>Retorno</h2>

**cdlc_id**: ID da base de destinos  
  
**cdlc_ctid**: ID do cliente da base de destinos  
  
**cdlc_name**: Nome da base de destino  
  
**cdlc_file**: Nome arquivo enviado se inserida por upload  
  
**cdlc_date**: Nome arquivo enviado se inserida por upload  
  
**cdlc_num**: Data do envio da base

<h2>Códigos e exemplos</h2>
### Method: POST
>```
>https://vox.velip.com.br/api/v2/GetDestinationsList
>```
### Headers

|Content-Type|Value|
|---|---|
|Content-Type|application/json|


### Headers

|Content-Type|Value|
|---|---|
|Authorization|Bearer |


### Body (**raw**)

```json
{"maxreg":"50","search":"teste"}
```

### 🔑 Authentication noauth

|Param|value|Type|
|---|---|---|



⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃

## End-point: GetCallStatus
<h2>Descritivo</h2>

A API GetCallStatus informa o resultado das ligações. Será retornado todas as ligações para cada destino da base de destinos ou envios individuais com os resultados se atendeu, tempos, horários e dígitos teclados em campanhas interativas. 

Pode também ser utilizado para reenviar os retornos (resultado) de uma campanha ou de envios individuais para a URL programada que receberá os retornos de cada  envio. 

<h2>Parâmetros</h2>

* **Para retorno de envios em lote por campanha:**

cp_id = [ID  da campanha pela plataforma  – Se informado apenas retorna da campanha]
ou 
cpid = [ID da campanha fornecido pelo cliente  ao gerar a campanha por API – Se informado apenas retorna do lote definido pelo cpid]

 * **Para retorno de envios individuais:**
Também é possível receber de um envio individual, nesses caso não é necessário informar um ID da campanha

cd_id = [ID da Plataforma]
ctid = [ID do envio  cliente]

 * **Para retorno de envios globais por período:**

date_start = [Opcional - data inicial da consulta – Para  envios gerais do período independente de campanhas ou cpid]
date_end = [Opcional - data final da consulta – Para  envios gerais do período independente de campanhas ou cpid]

 * **Parâmetros gerais:**

maxreg =  [Número de registros retornados. Se não informado limita em 1000 .  Para sem limites colocar 0 (zero) ]
rurl = [Opcional - URL de retorno -Será enviado o resultado para a URL. Se não informado o resultado é retornado na própria consulta em um JSON] 
onlydtmf =  [( Utilize =1 para receber apenas as ligações que o destino teclou algo) ]

<h2>Retorno</h2>

**cd_id**:  ID da ligação</br>
**cd_status**:  Status da ligação</br>
**cp_id**:  ID da campanha</br>
**cpid**: ID do cliente da campanha</br>
**ctid**:  ID do cliente da ligação</br>
**dest**:  Número telefônico discado</br>
**date**:  Data da ligação</br>
**time_dial**:  Hora da ligação </br>
**time_start**:  Hora do atendimento</br>
**time_end**:  Hora do fim da ligação</br>
**dur**:  Duração em segundos</br>
**route**:  Região discada</br>
**rate**:  Tarifa</br>
**value**:  Valor final da ligação</br>

 * **Códigos do cs_status:**

|     status       | Descritivo   |   
| :--------------:|:-------------:|
| OK| Ligação atendida |
| NA |Ligação não atendida|
| EK |Número incorreto ou faltando dígitos|
| IK |Número inexistente pela operadora|
| CK |Bloqueio de celular programado quando da configuração da campanha|
| BK |Bloqueio dos Procons - Não pertube|


<h2>Códigos e exemplos</h2>
### Method: POST
>```
>https://vox.velip.com.br/api/v2/GetCallStatus
>```
### Headers

|Content-Type|Value|
|---|---|
|Content-Type|application/json|


### Headers

|Content-Type|Value|
|---|---|
|Authorization|Bearer |


### Body (**raw**)

```json
{"date_start":"2020-12-25","date_end":"2021-01-10"}
```

### 🔑 Authentication noauth

|Param|value|Type|
|---|---|---|


### Response: 200
```json
{
    "return": {
        "status": "OK",
        "status_code": "0"
    },
    "calls": [
        {
            "cd_id": "c_92073",
            "cd_status": "NA",
            "cp_id": null,
            "cpid": "0",
            "ctid": "",
            "dest": "5511992069830",
            "date": "2021-03-04",
            "time_dial": "16:15:05",
            "time_start": "null",
            "time_end": "null",
            "dur": "0",
            "resp_1": "",
            "route": "null",
            "rate": "0,000",
            "value": "0,000"
        },
        {
            "cd_id": "c_92072",
            "cd_status": "NA",
            "cp_id": "0",
            "cpid": "0",
            "ctid": "",
            "dest": "5585999932703",
            "date": "2021-03-03",
            "time_dial": "08:31:51",
            "time_start": "null",
            "time_end": "null",
            "dur": "0",
            "resp_1": "",
            "route": "null",
            "rate": "0,000",
            "value": "0,000"
        },
        {
            "cd_id": "c_92071",
            "cd_status": "NA",
            "cp_id": "0",
            "cpid": "0",
            "ctid": "",
            "dest": "5585996249317",
            "date": "2021-03-03",
            "time_dial": "08:30:45",
            "time_start": "null",
            "time_end": "null",
            "dur": "0",
            "resp_1": "",
            "route": "null",
            "rate": "0,000",
            "value": "0,000"
        }
    ]
}
```


⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃

## End-point: MakeSMS
<h2>Descritivo</h2>

A API MakeSMS dispara um SMS individual. O envio de SMS também pode ser feito pelo painel de controle web.

<h2>Parâmetros</h2>

**dest** = \[Número do celular no formato Código do pais + Códido da cidade + Número (DDI+DDD+NUMERO)\]

**text** = \[Texto do SMS - Máximo 160 caracteres\]

**ctid** = \[OPCIONAL: ID único fornecido por quem envia para referencia - qualquer valor alfa-numérico até 15 caracteres\]

<h2>Retorno</h2>

**cdls_id**: ID do SMS

**Sempre que o status vier diferente de OK (ou status_code diferente de zero) o SMS não foi encaminhado.**

| statu | status_code | Details |
| --- | --- | --- |
| No sms account | 220 | Envio de SMS não liberado na conta |
| No dest | 230 | Sem o número do destino |
| No text | 235 | Sem o texto do SMS |
| Text more than 160 ch | 238 | Texto maior que 160 caracteres |
| Mobile is not valid | 240 | Número do celular inválido |

<h2>Códigos e exemplos</h2>
### Method: POST
>```
>https://vox.velip.com.br/api/v2/MakeSMS
>```
### Headers

|Content-Type|Value|
|---|---|
|Content-Type|application/json|


### Headers

|Content-Type|Value|
|---|---|
|Authorization|Bearer |


### Body (**raw**)

```json
{"dest":"5511992069830","text":"Este é um teste de SMS enviado por API","ctid":"123456"}
```

### 🔑 Authentication noauth

|Param|value|Type|
|---|---|---|



⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃

## End-point: GetUserID
<h2>Descritivo</h2>

A API GetUserID retorna um token com validade de 60 minutos para ser utilizado em acessos em que um aplicativo faz alguma operação diretamente sem intermediação de uma plataforma (server) intermediária.  
Também pode ser utilizado para validar se user and passowrd estão corretos.

O token tem validade de 60 minutos e é vinculado ao IP que gerou essa requisição, ou seja, se alguém em outro IP tentar usar, o token não será válido.

<h2>Parâmetros</h2>

**tsid** = \[Opcional - Se 1 irá gerar um token de acesso com validade de 60 min\]

<h2>Retorno</h2>

**cdcs_id**: ID da conta  
  
**cdcsu_id**: ID do usuário  
  
**aut_app**: Usuário tem permissão de usar app mobile  
  
**aut_send**: Usuário tem permissão de enviar mensagens individuais  
  
**aut_camp**: Usuário tem permissão de enviar mensagens em lote (campanhas)  
  
**tsid**: Token de acesso valido por 60 min e vinculado ao IP dessa requisição

<h2>Códigos e exemplos</h2>
### Method: POST
>```
>https://vox.velip.com.br/api/v2/GetUserID
>```
### Headers

|Content-Type|Value|
|---|---|
|Content-Type|application/json|


### Headers

|Content-Type|Value|
|---|---|
|Authorization|Bearer |


### Body (**raw**)

```json
{"tsid":"1"}
```

### 🔑 Authentication noauth

|Param|value|Type|
|---|---|---|


### Response: 201
```json
{
    "return": {
        "status": "OK",
        "status_code": "0",
        "cdcs_id": "2",
        "cdcsu_id": "7659",
        "aut_app": "1",
        "aut_send": "1",
        "aut_camp": "1",
        "tsid": "null"
    }
}
```


⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃ ⁃
