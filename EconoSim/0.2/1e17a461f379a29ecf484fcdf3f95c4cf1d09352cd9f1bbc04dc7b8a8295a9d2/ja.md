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

2つの残高間で等しい分割払いの債務契約を作成します。

  * creditor: 分割払いを受け取るバランスシート。
  * debtor: 分割払いが差し引かれるバランスシート。
  * interest_rate: 債務の利率。
  * installments: 分割払いの回数。
  * bank_debt: 債権者が銀行であるかどうか。
  * money_entry: 借りたお金を記録するために使用されるバランスシートのエントリ。
  * debt_entry: 債務を記録するために使用されるバランスシートのエントリ。
