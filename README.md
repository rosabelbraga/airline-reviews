# Análise de Sentimentos em Viagens Aéreas

Este projeto tem como objetivo desenvolver um sistema de análise de sentimentos com base em avaliações textuais de passageiros sobre companhias aéreas. A proposta é identificar aspectos positivos e negativos da experiência de voo, fornecendo insights valiosos para a melhoria contínua dos serviços prestados.

---

## Resumo dos resultados apresentados nos notebooks

### Processamento

- Remoção de amostras duplicadas e valores inválidos na coluna `overall_rating` (ex: 'n'). A base passou de 17.702 para 17.367 registros, mantendo 98% dos dados originais.
- Tratamento textual das colunas `review_title` e `review`.
- Geração de variáveis derivadas das colunas `review_date` e `date_flown`: dia da semana, ano-mês, ano, mês e diferença de dias entre as datas.
- Transformação de `overall_rating` em variáveis categóricas: `rating_category` e `rating_category_numeric` (Negativo = -1, Neutro = 0, Positivo = 1).
- Combinação de `review_title` e `review` na coluna `full_review_text`.
- Criação da variável `is_delay`, indicando possíveis atrasos com base em termos identificados em `full_review_text`.

### Análise Exploratória

- Correlação fraca entre as avaliações de serviços e `overall_rating` (corr. < 0.6).
- As subnotas estão altamente concentradas no valor 1.
- A média de `overall_rating` foi mais baixa em 2020, período marcado pela pandemia de COVID-19.
- Passageiros a negócios tendem a dar avaliações mais positivas.
- As percepções de passageiros de Economy Class e Premium Economy são semelhantes.
- Passageiros que voaram recentemente em relação à data do review tendem a avaliar mais negativamente.
- Reviews mais longos estão geralmente associados a sentimentos negativos.
- A presença de atrasos afeta o NPS de forma negativa.

### Modelos

- A coluna `wifi_e_connectivity` foi excluída devido ao alto número de valores ausentes.
- Foram aplicadas as seguintes técnicas: SMOTE para balanceamento das classes, `StandardScaler` para normalização dos dados numéricos e `TfidfVectorizer` para os dados textuais.
- Modelos utilizados: `LogisticRegression`, `RandomForestClassifier`, `MultinomialNB` e `GaussianNB`.
- Os modelos apresentaram acurácia média acima de 70%, com exceção do `GaussianNB` em dados numéricos.

### NPS

- A menção a atrasos nos reviews impactou negativamente o NPS em 89% dos casos analisados.

---

## Limitações

- Tempo reduzido para desenvolvimento da solução.

---

## Evoluções

- Refatoração do código 
- Realizar uma análise exploratória mais aprofundada.
- Testar abordagens alternativas de pré-processamento para dados textuais.
- Aplicar técnicas de otimização de hiperparâmetros e seleção de variáveis nos modelos.

---

## Como rodar localmente

### 1. Clone o repositório
```
    git clone https://github.com/rosabelbraga/airline-reviews.git
    cd airline-reviews
```

### 2. Crie o ambiente virtual

```
python -m venv .venv
    python -m venv .venv
    .venv\Scripts\activate # Linux: source .venv/bin/activate
```

### 3. Instale as depedências

```
pip install -r requirements.txt
```

### Requisitos

* Python 3.10+
