```
borrow(creditor::Balance,
    debtor::Balance,
    amount::Real,
    interest_rate::Real,
    installments::Integer,
    timestamp::Int64 = 0;
    bank_loan::Bool = true,
    money_entry::BalanceEntry = DEPOSIT,
    debt_entry::BalanceEntry = DEBT,
    negative_allowed::Bool = true)
```

Create a debt contract between 2 balance sheets and adjust the balance sheets according to the parameters of the debt contract.

  * creditor: the balance sheet receiving the installments.
  * debtor: the balance sheet from which the installments will be subtracted.
  * amount: the amount to be borrowed.
  * interest_rate: the interest rate on the debt.
  * installments: the number of installments.
  * interval: the interval between the installments.
  * timestamp: the current timestamp.
  * bank_loan: indicates whether the creditor is a bank. If this is true new money is created to supply the money to the debtor. If this is false, money is transferred from the creditor to the debtor.
  * negative_allowed: When this is true, a debtor can lend out money even when it would result in the creditor's money entry becoming negative. Otherwise only the amount available will be lent out. In case of bank loans this is ignored.
  * money_entry: the balance sheet entry to be used to book the borrowed money.
  * debt_entry: the balance sheet entry to be used to book the debt.
