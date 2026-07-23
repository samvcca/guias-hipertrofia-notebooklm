# Caderno Temático: Análise de Dados e Ciência do Treinamento Resistido e Nutrição para Hipertrofia via NotebookLM
## 1. Contexto e Objetivos
Este repositório apresenta o resultado do desenvolvimento de um **Caderno Temático no NotebookLM**, elaborado como parte do desafio prático do Bootcamp de Inteligência Artificial / GenAI da DIO.
Este projeto tem como foco a **Ciência do Treinamento de Força, Nutrição Esportiva e Hipertrofia Muscular**, unida à aplicação prática de **Inteligência Artificial Generativa** e **Análise de Dados**.
### Objetivos Principais:
* **Curadoria Científica:** Consolidar e analisar literaturas científicas sobre síntese proteica muscular (SPM), autorregulação do treino de força (VBT, RIR/PSE), prevenção de overtraining (*deload*) e composição de alimentos.
* **Engenharia de Prompts e Troubleshooting:** Testar a capacidade de extração, estruturação e síntese do LLM, identificando falhas de resposta, limitações de renderização de interface e ausência de dados nativos na literatura.
* **Miniguia de Estudos:** Produzir um material consolidado em formato de resumos estruturados, glossário e biblioteca de prompts reutilizáveis para futuras revisões teóricas e práticas.
---
## 2. Curadoria de Fontes
Foram selecionados 5 documentos abertos (PDFs) cobrindo bases nutricionais, fisiológicas e metodológicas do treinamento de força:

| # | Fonte / Autores | Tipo de Documento | Foco Central no Caderno |
| :--- | :--- | :--- | :--- |
| **1** | LIRA, Kenny Judson Cruz de (UFRN, 2025) | Revisão de Literatura (TCC) | *Influência do Tipo de Proteína (Animal vs. Vegetal) sobre o Aumento e Manutenção da Massa Muscular*. |
| **2** | DOMINGUES, Letícia (UNOPAR, 2023) | Dissertação e Relatório Técnico | *Proteína e Aumento da Massa Muscular em Praticantes de Exercícios Resistidos e Recomposição Corporal*. |
| **3** | COSTA, Mateus Cordeiro et al. (UFAL/UFRPE, 2025) | Periódico | *Autorregulação no Treinamento de Força: Métodos Objetivos (TBV/Perda de Velocidade) e Subjetivos (RIR/PSE)*. |
| **4** | REIS, Magnelson Bonfim et al. (UNIGRAN, 2023) | Artigo Científico | *Overtraining e o Método De-Load: Estratégias para Recuperação e Reparação Muscular e Articular*. |
| **5** | NEPA / UNICAMP (4ª Ed., 2011) | Guia / Tabela de Composição de Alimentos | *Tabela Brasileira de Composição de Alimentos (TACO)*: Densidade nutricional e aminogramas. |

---
## 3. Engenharia de Prompts e Cicatrizes (Troubleshooting)
Esta seção documenta a evolução da interação com a IA no NotebookLM, registrando o diagnóstico do comportamento do modelo, o refinamento dos comandos e o tratamento de falhas de renderização ou conteúdo.
### Caso 1: Mapeamento de Recomendação e Distribuição Proteica
* **Prompt Vago (Iteração 1):**  
  > *"Quanto de proteína eu preciso comer por dia para ganhar massa?"*
* **Resposta Obtida da IA:** Resposta em texto corrido e marcadores simples, citando faixas genéricas da ISSN (1,4 a 2,0 g/kg/dia) e ACSM (1,2 a 2,0 g/kg/dia).
* **Diagnóstico / Cicatriz:** O texto corrido exigia leitura densa para extrair e comparar métricas específicas entre perfis de praticantes e estratégias de timing.
* **Prompt Refinado (Iteração 2):**  
  > *"Com base exclusivamente nas fontes do caderno sobre nutrição esportiva, extraia a recomendação exata de ingestão diária de proteína (g/kg/dia) para hipertrofia muscular. Monte uma tabela comparativa com 3 colunas: Perfil do Praticante, Recomendação (g/kg/dia) e Distribuição por Refeição."*
* **Resultado & Troubleshooting Técnico:** A IA estruturou a matriz dividindo entre Praticante Geral, Praticante Treinado (1,6 a 2,2 g/kg/dia) e Dieta Hipocalórica (2,2 a 3,0 g/kg/dia). Porém, o refinamento revelou um bug no renderizador Markdown do NotebookLM: as quebras de linha enviadas como `<br>` foram exibidas como texto puro dentro das células da tabela. 
* **Ação Corretiva:** Sanitização manual do texto exportado antes da publicação no repositório.
---
### Caso 2: Calibração de Volume de Treino, Níveis de Experiência e RIR
* **Prompt Vago (Iteração 1):**  
  > *"Quantas séries eu devo fazer na academia por semana?"*
* **Resposta Obtida da IA:** Listou faixas amplas (baixo: $\le 9$ séries; moderado: 10-20; alto: 20-30; muito alto: $> 30$) e explicou conceitos teóricos como Volume Mínimo Efetivo (VME) e Volume Máximo Recuperável (VMR).
* **Diagnóstico / Cicatriz:** A IA não relacionou o volume aos níveis de experiência (iniciante, intermediário, avançado) nem abordou a métrica de esforço (RIR).
* **Prompt Refinado (Iteração 2):**  
  > *"Analise o artigo de treinamento de força carregado e responda: Qual é a faixa de volume semanal de séries de trabalho por agrupamento muscular recomendada para maximizar a hipertrofia? Diferencie os valores entre iniciantes, intermediários e avançados, e explique o conceito de Repetições de Reserva (RIR) aplicado a essas séries."*
* **Resultado & Diagnóstico de Alucinação Evitada:** O refinamento forçou o LLM a declarar uma lacuna da literatura presente nos PDFs: **as fontes não fixam uma contagem de séries isolada exclusivamente por nível de praticante**, mas sim limites individuais e zonas de intensidade (% de 1RM). A IA explicou o RIR como método subjetivo de autorregulação, destacando a falta de precisão perceptual em iniciantes (tendência a subestimar a proximidade da falha).
---
## 4. Miniguia de Estudo (Entrega Final)
### 4.1. Resumos Estruturados
#### A. Síntese Proteica e Nutrição para Hipertrofia
* **Volume Diário Proteico:** Praticantes de treinamento resistido visando hipertrofia necessitam de **1,4 a 2,0 g/kg/dia** (ISSN/ACSM), com platô otimizado em **1,6 a 2,2 g/kg/dia** para indivíduos treinados.
* **Preservação em Déficit Calórico:** Em dietas hipocalóricas, a necessidade eleva-se para **2,2 a 3,0 g/kg/dia** para mitigar o catabolismo muscular.
* **Distribuição e Leucina:** Fracionamento em 3 a 5 refeições contendo de **20g a 40g de proteína por refeição** (ou $0,25\text{ a }0,55\text{ g/kg}$), garantindo o gatilho anabólico da via **mTOR** através de doses de **2,5g a 3g de leucina**.
* **Equivalência Animal vs. Vegetal:** Fontes vegetais isoladas (como ervilha e soja) promovem ganhos de massa magra e força equivalentes às proteínas animais (whey/carne), desde que a dose total diária e o aporte de leucina sejam equiparados.
#### B. Variáveis do Treinamento de Força e Autorregulação
* **Estímulo Primário:** A **Tensão Mecânica** (mecanotransdução) é o pilar central para a biogênese ribossomal e hipertrofia.
* **Faixas de Intensidade:** Cargas entre 60% e 85% de 1RM (8 a 12 repetições) são ideais para segurança e conforto, embora intensidades a partir de 30% de 1RM promovam hipertrofia similar se levadas próximas à falha.
* **Autorregulação Subjetiva (RIR/PSE):** Permite ajustar o peso com base no número de repetições estimadas até a falha concêntrica, adaptando a sessão à fadiga residual diária.
* **Treinamento Baseado em Velocidade (TBV):** Medida objetiva em que a Perda de Velocidade (PV) da barra controla a fadiga intra-série. Limiares de PV $> 30\%$ geram mais hipertrofia, mas causam maior fadiga metabólica.
#### C. Gestão da Fadiga e Estratégia de *Deload*
* **Prevenção do Overtraining:** Treinos contínuos de alta intensidade sem pausas regenerativas levam à Síndrome de Overtraining (queda de rendimento, dores articulares e alterações do sono).
* **Modalidades de Deload:** 
  * *Ativo (Redução de Volume/Intensidade):* Redução de 50% nas cargas ou séries, ou inclusão de aeróbicos leves ($<50\%\text{ FC}_{\max}$). Apresenta melhores resultados na manutenção e ganho de desempenho.
  * *Passivo (Cessação Total):* Parada de 7 dias. Apresenta atenuação superior na percepção de dores articulares e musculares (redução de até 81,9% nos relatos de dores frequentes).
---
### 4.2. Glossário de Conceitos
* **SPM (Síntese Proteica Muscular):** Processo biológico de construção de tecido muscular impulsionado pelo treino resistido e disponibilidade de aminoácidos essenciais.
* **mTOR (Mammalian Target of Rapamycin):** Via sinalizadora celular primária que ativa a síntese proteica quando estimulada por tensão mecânica e aminoácidos (leucina).
* **RIR (Reps in Reserve / Repetições de Reserva):** Indicador de intensidade perceptiva que mensura quantas repetições adicionais o praticante conseguiria realizar antes da falha concêntrica.
* **TBV (Treinamento Baseado em Velocidade):** Método objetivo de prescrição em que o monitoramento da velocidade da barra determina o % de 1RM e o nível de fadiga.
* **Deload:** Período planejado de redução intencional na carga de treino (volume/intensidade) ou descanso total para promover reparação articular/neuromuscular.
* **Recomposição Corporal:** Ganho concomitante de massa muscular esquelética e redução de massa gorda.
---
### 4.3. Prompts Reutilizáveis para Revisões Futuras
1. **Auditoria Nutricional de Macronutrientes:**
   > *"Atuando como um nutricionista esportivo analise o texto X. Tenho [X] kg e meu objetivo é hipertrofia em superávit calórico. Com base nas tabelas da TACO e diretrizes da ISSN do caderno, estruture uma divisão diária de macronutrientes (proteínas, carboidratos e gorduras) especificando a gramatura por refeição."*
2. **Avaliação de Treino e Estratégia de Autorregulação:**
   > *"Analise a seguinte divisão de treino: [Inserir Treino]. Com base nos capítulos de autorregulação e volume, identifique se a quantidade de séries está dentro da faixa ajustada de 10-20 séries/semana por músculo e sugira uma escala de RIR (Repetições de Reserva) para cada exercício."*
3. **Diagnóstico de Fadiga e Prescrição de Deload:**
   > *"Com base no estudo experimental sobre overtraining e deload, analise os seguintes sintomas: [Listar Sintomas, ex: dores articulares frequentes, queda de carga]. Recomende a estratégia de Deload mais adequada (Ativo vs. Passivo) detalhando o protocolo de aplicação de 7 dias."*
