
# FitMetric — Sistema Móvel

O "FitMetric" é uma solução digital em formato de aplicativo móvel voltada para democratizar, simplificar e acelerar a avaliação física, motora e nutricional de crianças e jovens de 6 a 17 anos. O aplicativo é baseado estritamente na metodologia científica do Projeto Esporte Brasil (PROESP-Br), substituindo as anotações em papel por uma interface inteligente que realiza cálculos instantâneos de saúde e desempenho motor diretamente na quadra.

---

##  Links do Projeto
* **Protótipo Interativo no Figma (V1): https://www.figma.com/make/xVPbdk1wtDXcWj6Ltf93N6?node-id=0:1&p=f&t=9BLxdE4DAs8ANXK5-0&fullscreen=1&type=figmake

---

##  Equipe e Funções
* **Integrante 1:** Vinícius- Product Owner / Analista de Requisitos
* **Integrante 2:** Vinícius - Scrum Master / Designer UI-UX
* **Integrante 3:** Manoel- Desenvolvedor Mobile Front-End
* **Integrante 4:** alberto - Desenvolvedor Back-End / Banco de Dados

---

##  Requisitos Funcionais (RF)
* **RF01 - Cadastro de Alunos:** O professor deve conseguir cadastrar alunos de 6 a 17 anos (Nome, Idade, Sexo).
* **RF02 - Coleta de Dados Brutos:** O sistema deve permitir a inserção de medidas corporais brutas (Massa Corporal e Estatura) e resultados dos testes práticos.
* **RF03 - Cronômetro Integrado:** O app deve possuir um cronômetro nativo na tela para os testes de corrida/velocidade com alertas sonoros.
* **RF04 - Modo Offline:** O aplicativo deve coletar os dados na quadra mesmo sem internet e sincronizar quando houver conexão.
* **RF05 - Cálculo Instantâneo de Saúde:** O sistema deve calcular automaticamente o IMC e a Razão Cintura-Estatura com base nas diretrizes do PROESP-Br.
* **RF06 - Classificação de Desempenho:** O sistema deve mapear e classificar o desempenho motor instantaneamente em: Fraco, Razoável, Bom, Muito Bom ou Excelência.
* **RF07 - Geração de Gráfico Visual:** Exibir na tela se o estudante está na "Zona Saúde" ou na "Zona de Risco à Saúde".
* **RF08 - Relatório para Pais:** Gerar um relatório simples em formato PDF para ser enviado via WhatsApp aos responsáveis.
* **RF09 - Relatório Consolidado para a Direção:** Gerar relatórios estatísticos da comunidade escolar (ex: "% de alunos na zona de risco").

---

##  Casos de Uso (Engenharia de Software):

### Caso de Uso 01 (UC01): Manter Cadastro de Alunos
* **RF Atendido:** RF01
* **Ator:** Professor
* **Fluxo Normal:** O professor acessa a aba de alunos, clica em "Novo Aluno", insere Nome, Idade e Sexo, e clica em Salvar. O sistema valida os dados e armazena o registro no banco de dados.

### Caso de Uso 02 (UC02): Registrar Avaliação Física e Prática
* **RFs Atendidos:** RF02, RF05, RF06 e RF07
* **Ator:** Professor
* **Fluxo Normal:** O professor seleciona um aluno, insere a Massa Corporal e Estatura, e digita os resultados dos testes. Ao salvar, o sistema calcula na hora o IMC/Razão Cintura-Estatura, gera a classificação de desempenho motor e plota o gráfico visual da "Zona Saúde" ou "Zona de Risco" na tela.

### Caso de Uso 03 (UC03): Utilizar Cronômetro com Alerta Sonoro
* **RF Atendido:** RF03
* **Ator:** Professor
* **Fluxo Normal:** Na tela do teste de corrida, o professor aciona o botão de início do cronômetro nativo. O app inicia a contagem e, ao atingir o tempo limite ou ser pausado, emite um apito automático e joga o tempo direto no campo do teste.

### Caso de Uso 04 (UC04): Sincronizar Dados em Modo Offline
* **RF Atendido:** RF04
* **Ator:** Professor (Automático pelo sistema)
* **Fluxo Normal:** Sem internet na quadra, o professor faz as avaliações normalmente. O app salva tudo no banco local do celular. Assim que o aparelho detecta sinal de internet (Wi-Fi ou 4G), o sistema envia os dados locais automaticamente para a nuvem.

### Caso de Uso 05 (UC05): Emitir Relatório para Pais via PDF
* **RF Atendido:** RF08
* **Ator:** Professor
* **Fluxo Normal:** O professor entra no perfil do aluno avaliado, clica em "Enviar Relatório", o sistema gera um arquivo PDF lúdico e simplificado com os resultados e abre o menu de compartilhamento do WhatsApp para envio direto aos responsáveis.

### Caso de Uso 06 (UC06): Consultar Gráfico Estatístico da Escola
* **RF Atendido:** RF09
* **Ator:** Direção da Escola / Coordenação
* **Fluxo Normal:** O diretor faz login, escolhe uma turma (ex: 6º Ano) e clica em Gerar Relatório. O sistema processa todas as avaliações daquela turma e exibe gráficos consolidados mostrando a porcentagem geral de alunos que estão em zona de risco ou saudável.
* **Fluxo Alternativo:** Se a turma selecionada não tiver nenhuma avaliação feita, o sistema barra a geração e avisa: *"Dados insuficientes para esta turma"*.

---

##  Diagrama de Caso de Uso do Sistema:

```mermaid
graph TD
    %% Definição dos Atores
    Professor((Professor de Ed. Física))
    Direcao((Direção / Coordenação))

    %% Limite do Sistema FitMetric
    subgraph Aplicativo FitMetric
        UC01(UC01: Manter Cadastro de Alunos)
        UC02(UC02: Registrar Avaliação Física e Prática)
        UC03(UC03: Utilizar Cronômetro com Alerta Sonoro)
        UC04(UC04: Sincronizar Dados em Modo Offline)
        UC05(UC05: Emitir Relatório Individual para Pais via PDF)
        UC06(UC06: Consultar Gráfico Estatístico da Escola)
    end

    %% Associações dos Atores com os Casos de Uso
    Professor --> UC01
    Professor --> UC02
    Professor --> UC03
    Professor --> UC04
    Professor --> UC05

    Direcao --> UC06
