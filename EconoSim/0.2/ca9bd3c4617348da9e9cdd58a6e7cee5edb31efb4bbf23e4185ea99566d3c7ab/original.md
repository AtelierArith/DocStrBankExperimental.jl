```
mutable struct Debt
```

A transferable debt contract between two balance sheets.

  * id: The unique id of the contract
  * creditor: the balance sheet which receives debt payments.
  * debtor: the balance sheet from which payments are deducted.
  * installments: a list of installments to be paid.
  * interest_rate: the interest rate on the debt.
  * bank_debt: indicates whether the debt is to a bank. This has an impact on how the initial transfer of money and the downpayments are booked to the creditor's balance sheet.
  * money_entry: the entry to be used to book the borrowed money.
  * debt_entry: the entry to be used to book the debt.
  * creation: the timestamp of the creation of the debt.
  * interval: the interval between installments. This can be 0.
