# Projeto_Final-Dataset_Cyclistic_Bike_Share

🎯 Objetivo do Projeto
Este projeto utiliza técnicas de aprendizado de máquina supervisionado para resolver um problema de negócio real da Cyclistic, uma empresa de compartilhamento de bicicletas. O objetivo principal é desenvolver um modelo de classificação capaz de prever se um usuário é do tipo casual ou membro com base nos dados de suas viagens. A solução visa fornecer insights para a equipe de marketing otimizar campanhas de conversão de usuários casuais em membros anuais, que são mais lucrativos.

📊 Dataset
O estudo foi realizado com base em um conjunto de dados público da Divvy Tripdata, que inclui os dados da Cyclistic.

Fonte: Kaggle: Divvy Tripdata

Arquivo Utilizado: 202104-divvy-tripdata.csv

🛠️ Metodologia e Etapas Executadas
O projeto foi estruturado seguindo um pipeline clássico de Ciência de Dados, garantindo robustez e reprodutibilidade.

<!-- Você pode fazer upload do seu fluxograma para um site como o imgur.com e colocar o link aqui -->

1. Análise Exploratória de Dados (EDA)
Objetivo: Entender a estrutura dos dados, identificar padrões iniciais e detectar problemas como valores ausentes e outliers.

Ações:

Geração de estatísticas descritivas.

Visualização da distribuição da variável alvo (member_casual).

Análise de padrões de uso por dia da semana e hora do dia.

Identificação de um padrão claro: membros usam o serviço para transporte durante a semana, enquanto casuais usam para lazer nos fins de semana.

2. Pré-processamento e Engenharia de Features
Objetivo: Limpar os dados e criar novas variáveis (features) com maior poder preditivo.

Ações:

Conversão de colunas de data/hora (started_at, ended_at) para o formato datetime.

Criação de Features:

trip_duration_minutes: Duração da viagem em minutos.

day_of_week: Dia da semana da viagem.

hour_of_day: Hora do dia em que a viagem começou.

Limpeza: Remoção de viagens com duração negativa ou extremamente longa (outliers).

Codificação: Transformação de variáveis categóricas (rideable_type, day_of_week) em formato numérico usando One-Hot Encoding (drop_first=True para evitar multicolinearidade).

3. Treinamento e Avaliação dos Modelos Base
Objetivo: Comparar diferentes algoritmos para identificar o mais promissor.

Ações:

Divisão dos dados em 80% para treino e 20% para teste (stratify=y).

Escalonamento das features com StandardScaler.

Treinamento de três modelos:

Regressão Logística (baseline)

Random Forest

XGBoost

Avaliação: Comparação dos modelos com base na métrica ROC-AUC. O XGBoost foi selecionado como o campeão.

4. Ajuste de Hiperparâmetros (Otimização)
Objetivo: Extrair o máximo de performance do modelo campeão.

Ações:

Utilização do RandomizedSearchCV para testar 50 combinações de hiperparâmetros do XGBoost.

Treinamento e seleção da melhor configuração com base na performance em validação cruzada.

5. Análise do Modelo Final e Redução de Dimensionalidade
Objetivo: Avaliar em profundidade o modelo final e testar técnicas de simplificação.

Ações:

Análise do XGBoost Otimizado com Matriz de Confusão e Feature Importance.

Aplicação da técnica de PCA (Principal Component Analysis) para reduzir o número de features e comparação do desempenho antes e depois da redução.

Conclusão da Análise: O modelo completo, com todas as features, manteve a performance superior.

📈 Resultados
O modelo final (XGBoost Otimizado) alcançou um excelente desempenho, demonstrando alta capacidade de distinguir os dois tipos de usuários:

ROC-AUC: 0.754

Acurácia: 71.0%

As features mais importantes para a previsão do modelo foram, em ordem:

Duração da Viagem (trip_duration_minutes)

Dia da Semana (day_of_week)

Hora do Dia (hour_of_day)

🚀 Como Executar o Projeto
Pré-requisitos
Python 3.x

Jupyter Notebook ou Google Colab

Instalação
Clone este repositório e instale as dependências necessárias.

git clone https://github.com/seu-usuario/seu-repositorio.git
cd seu-repositorio
pip install -r requirements.txt

(Nota: Crie um arquivo requirements.txt com as bibliotecas usadas: pandas, numpy, matplotlib, seaborn, scikit-learn, xgboost)

Execução
Coloque o dataset 202104-divvy-tripdata.csv na pasta raiz do projeto.

Abra o notebook nome_do_seu_notebook.ipynb e execute as células em ordem.

🏁 Conclusão
O projeto demonstrou com sucesso que os dados de viagem contêm padrões de comportamento claros e preditivos. O modelo desenvolvido pode ser uma ferramenta valiosa para a Cyclistic, permitindo a criação de campanhas de marketing mais inteligentes e personalizadas, com o objetivo final de aumentar a conversão de usuários casuais em membros an
