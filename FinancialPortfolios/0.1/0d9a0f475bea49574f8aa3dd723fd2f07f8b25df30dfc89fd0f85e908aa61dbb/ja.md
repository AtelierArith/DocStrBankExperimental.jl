```
update!(fp::FinancialPortfolio,ret)
```

ポートフォリオのウェイトをその場で更新します。期間ポートフォリオリターンを返します。

ポートフォリオは、供給された資産リターンのサブセットのみを含むことが許可されていますが、その逆は許可されていません。

***例***

```
w = [0.5, 0.25, 0.25]
r = [0.1, 0.1, -0.1]
FP = FinancialPortfolio(w)
update!(FP,r)
FP
```
