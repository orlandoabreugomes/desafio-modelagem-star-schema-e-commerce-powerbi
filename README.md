# Modelagem de um Dashboard de E-commerce com Power BI utilizando fórmulas DAX


ℹ️ **Nota:** Este projeto foi desenvolvido durante o curso “Modelagem de Dados com o Power BI” ministrado por [Juliana Mascarenhas](https://www.linkedin.com/in/juliana-mascarenhas-ds/) na [DIO](https://web.dio.me).

## 1. Criação da Tabela `D_Calendário` com DAX

Foi realizada a criação de uma tabela de calendário utilizando o comando DAX para 
garantir a integridade e a continuidade das datas dentro do modelo de dados. Essa 
tabela será utilizada para fornecer contexto temporal no modelo de **star schema**.

A tabela foi criada com a função `CALENDAR`, que gera um intervalo de datas com base nas datas mínima e máxima da tabela de transações (`Financial Sample`).

### Comando DAX utilizado:

```DAX
D_Calendário = CALENDAR(MIN('financials_origem'[Date]), MAX('financials_origem'[Date]))

```

## 2. Criação do Índice na Tabela `D_Produtos`

Foi criada uma nova coluna de **Índice de Produtos** na tabela de dimensões `D_Produtos` para facilitar o relacionamento entre as tabelas e melhorar a navegação no modelo de dados. O índice foi gerado utilizando uma regra condicional de busca de correspondências entre três colunas principais nas tabelas de produtos: **Produto**, **Segmento** e **País**.

A nova coluna foi criada com o seguinte comando DAX:

### Comando DAX utilizado:

```DAX
sk_id_f_vendas = 
LOOKUPVALUE(
    F_Vendas[SK_ID], 
    F_Vendas[ Sales], D_Detalhes[ Sales],
    F_Vendas[Country], D_Detalhes[Country],
    F_Vendas[Segment], D_Detalhes[Segment],
    F_Vendas[Product], D_Detalhes[Product]
    )
```
## 3. Conclusão

A tabela `D_Calendário` foi criada com sucesso usando o DAX, permitindo uma melhor análise temporal. Além disso, a criação do índice na tabela `D_Produtos` facilita o relacionamento entre as tabelas de dimensões e fatos, permitindo um modelo de dados mais organizado e eficiente no formato star schema.

Esses ajustes são essenciais para garantir que o modelo de dados funcione de forma otimizada, proporcionando um melhor desempenho nas consultas e análises.



![Star Schema](https://github.com/orlandoabreugomes/desafio-modelagem-star-schema-e-commerce-powerbi/blob/main/deafio_star_schema_financial_sample.png)


## 🖥️ Tecnologias utilizadas no Projeto:

* [Power BI](https://www.microsoft.com/pt-br/power-platform/products/power-bi)


## 🙍🏽 Profissional
Orlando Gomes
[GitHub](https://github.com/orlandoabreugomes) | [Linkedin](https://www.linkedin.com/in/orlandoabreugomes/) | [e-mail](mailto:gomes.oa@gmail.com)
