```
Debt(creditor::Balance,
    debtor::Balance,
    amount::Real,
    interest_rate::Real,
    installments::Integer;
    bank_debt::Bool = true,
    money_entry::BalanceEntry = DEPOSIT,
    debt_entry::BalanceEntry = DEBT,
    creation::Int64 = 0,
    interval::Int64 = 0)
```

Create a debt contract between two balances with a number of equal installments.

  * creditor: the balance sheet receiving the installments.
  * debtor: the balance sheet from which the installments will be subtracted.
  * interest_rate: the interest rate on the debt.
  * installments: the number of installments.
  * bank_debt: whether or not the creditor is a bank.
  * money_entry: the balance sheet entry to be used to book the borrowed money.
  * debt_entry: the balance sheet entry to be used to book the debt.
