---
title: "Objetos da Simulação de Pagamento"
slug: "objetos-simulação-de-pagamento"
hidden: false
date: 2020-04-14T14:26:24.270Z
lastmod: 2021-08-26T12:35:24.621Z
weight: 3
---

---
<br>

O Dry Run de pagamentos retorna, além do [Objeto Pagamento]({{< relref "/docs/referencia-da-api/pagamentos/overview/#o-objeto-pagamento">}}) em si, os Objetos [Barcode Details](#objeto-barcode-details) e [Details](#objeto-details).

Como complemento, descrevemos os possíveis resultados para o campo [document_payment_type](#document_payment_type).

<br>

### Objeto Barcode Details
---

<br>

O Objeto Barcode Details é composto por meio da extração das informações contidas no código de barras informado, dispondo-as nos seguintes campos:

<br>

| Chave           | Descrição                                                                 | Tipo      |
| --------------- | ------------------------------------------------------------------------- | --------- |
| bank_code       | Código numérico da instituição que emitiu o documento.                    | _String_  |
| bank_name       | Nome da instituição que emitiu o documento.                               | _String_  |
| barcode         | Código de barras.                                                         | _String_  |
| expiration_date | Data de vencimento.                                                       | _String_  |
| face_value      | Valor com o qual o documento foi criado e que consta do código de barras. | _Integer_ |
| writable_line   | Código numérico que acompanha o código de barras.                         | _String_  |

<br>

### Objeto Details
---

<br>

O Objeto Details traz informações do status atual desse documento segundo sua fonte emissora, como juros, multas, horário limite de pagamento, entre outras. Veja todas as informações retornadas abaixo.

<br>

| Chave                  | Descrição                                                                                                                                                                            | Tipo      |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------- |
| bank_name              | Nome da instituição que emitiu o documento.                                                                                                                                          | _String_  |
| barcode                | Código de barras.                                                                                                                                                                    | _String_  |
| discount_value         | Valor do desconto que está sendo aplicado ao boleto. Caso nenhum desconto esteja sendo aplicado vira `null`.                                                                           | _Integer_ |
| document_payment_type  | Informa o código referente a título.					| _Integer_	|
| document_type          | Informa o tipo de documento. Valores possíveis são: boleto e concessionaria.                                                                                                         | _String_  |
| expiration_date        | Data de vencimento    | _String_  |
| face_value             | Valor com o qual o documento foi criado e que consta do código de barras.        | _Integer_ |
| fine_value             | Valor da multa que está sendo aplicada ao boleto. Caso nenhuma multa esteja sendo aplicada vira `null`.     | _Integer_ |
| interest_value         | Valor dos juros que estão sendo aplicados ao boleto. Caso não haja juros aplicados vira `null`.            | _Integer_ |
| max_value              | Valor máximo que será aceito no pagamento deste documento.                        | _Integer_ |
| min_value              | Valor mínimo que será aceito no pagamento deste documento.                 | _Integer_ |
| payer_cpf_cnpj         | Número do documento do pagador sem pontos.                     | _String_  |
| payer_legal_name       | É o nome que identifica o pagador para fins legais, administrativos e outros fins oficiais.                                                                                          | _String_  |
| payer_trade_name       | Nome fantasia do pagador.                                                                                                                                                            | _String_  |
| payment_end_time       | Horário até o qual o pagamento é possível em um dia útil. Respeita o payment_limit_date. Formato hh:mm:ss.                                                                           | _String_  |
| payment_limit_date     | Data limite para pagamento do documento. Formato ISO8601 "YYYY-MM-DD".                                                                                                               | _String_  |
| payment_start_time     | Horário a partir do qual o pagamento é possível em um dia útil. Respeita o payment_limit_date. Formato hh:mm:ss.                                                                     | _String_  |
| recipient_cpf_cnpj     | Número do documento do beneficiário sem pontos.                                                                                                                                      | _String_  |
| recipient_name         | Nome do beneficiário.                                                                                                                                                                | _String_  |
| settlement_date        | Data em que o dinheiro do pagamento do boleto é depositado na conta do beneficiário. Formato ISO8601 "YYYY-MM-DDThh:mm:ssZ". Caso o boleto ainda não tenha sido pago voltará `null`. | _String_  |
| status                 | Status atual do documento na sua instituição emissora. Valores possíveis: payable, paid ou unpayable.                                                                                | _String_  |
| total_added_value      | Total que foi adicionado ao valor original do documento decorrente de juros e multas.                                                                                                | _Integer_ |
| total_discounted_value | Total que foi abatido do valor originial do documento decorrente de descontos.                                                                                                       | _Integer_ |
| updatable_value        | Indica se é permitido alterar o valor do documento. Só disponível para document_type com valor concessionaria.                                                                       | _Boolean_ |
| value                  | Valor atualizado já com descontos, multas e juros que se aplicam.                                                                                                                    | _Integer_ |
| writable_line          | Código numérico que acompanha o código de barras.                                                                                                                                    | _String_  |
| unpayable_reason_code  | Código que representa o motivo de estar impagável. | _String_	|
| unpayable_reason_description | Descrição do motivo de estar impagável. | _String_	| 
| accepts_partial_payment | Indica se o boleto aceita pagamento parcial                       | _Boolean_ |
| number_of_partials | Indica quantas vezes o boleto pode ser pago, se o número for 99 significa que o número de vezes é ilimitado | _Integer_ |


<br>

### Document_payment_type
---

<br>


<br>

| Domínio           | Descrição                                     |
| ----------------- | --------------------------------------------- |
| 1					| CH Cheque.									|
| 2					| DM Duplicata Mercantil.						|
| 3					| DMI Duplicata Mercantil Indicação.			|
| 4					| DS Duplicata de Serviço.						|
| 5					| DSI Duplicata de Serviço Indicação.			|
| 6					| DR Duplicata Rural.							|
| 7					| LC Letra de Câmbio.							|
| 8					| NCC Nota de Crédito Comercial.				|
| 9					| NCE Nota de Crédito Exportação.				|
| 10				| NCI Nota de Crédito Industrial.				|
| 11				| NCR Nota de Crédito Rural.					|
| 12				| NP Nota Promissória.							|
| 13				| NPR Nota Promissória Rural.					|
| 14				| TM Triplicata Mercantil.						|
| 15				| TS Triplicata de Serviço.						|
| 16				| NS Nota de Seguro.							|
| 17				| RC Recibo.									|
| 18				| FAT Bloqueio.									|
| 19				| ND Nota de Débito.							|
| 20				| AP Apólice de Seguro.							|
| 21				| ME Mensalidade Escolar.						|
| 22				| PC Parcela de Consórcio.						|
| 23				| NF Nota Fiscal.								|
| 24				| DD Documento de Dívida.						|
| 25				| Cédula de Produto Rural.						|				
| 26				| Warrant.										|
| 27				| Dívida Ativa de Estado.						|
| 28				| Dívida Ativa do Município.					|
| 29				| Dívida Ativa da União.						|
| 30				| Encargos Condominiais.						|
| 31				| Cartão de Crédito.							|
| 32				| Boleto Proposta.								|
| 33				| Boleto de Depósito e Aporte.					|
| 99				| Outros.										|