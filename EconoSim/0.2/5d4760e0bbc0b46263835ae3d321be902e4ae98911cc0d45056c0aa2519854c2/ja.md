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

2つのバランスシート間で債務契約を作成し、債務契約のパラメータに従ってバランスシートを調整します。

  * creditor: 分割払いを受け取るバランスシート。
  * debtor: 分割払いが差し引かれるバランスシート。
  * amount: 借りる金額。
  * interest_rate: 債務の利率。
  * installments: 分割払いの回数。
  * interval: 分割払いの間隔。
  * timestamp: 現在のタイムスタンプ。
  * bank_loan: 債権者が銀行であるかどうかを示します。これが真であれば、債務者に資金を供給するために新しいお金が創出されます。これが偽であれば、債権者から債務者にお金が移転されます。
  * negative_allowed: これが真であれば、債務者は債権者の資金エントリが負になる場合でもお金を貸し出すことができます。そうでなければ、利用可能な金額のみが貸し出されます。銀行ローンの場合は無視されます。
  * money_entry: 借りたお金を記録するために使用されるバランスシートエントリ。
  * debt_entry: 債務を記録するために使用されるバランスシートエントリ。
