```
portfolioreturn(fp::FinancialPortfolio,ret)
```

加重ポートフォリオリターンを計算します。ポートフォリオのウェイトに名前や識別子がある場合、リターンにもそれが必要です。ポートフォリオは、提供された資産リターンのサブセットのみを含むことが許可されていますが、その逆は許可されていません。

***例***

```
w = [0.5, 0.25, 0.25]
r = [0.1, 0.1, -0.1]
FP = FinancialPortfolio(w)
portfolioreturn(FP,r)
```
