```
update!(fp::FinancialPortfolio,ret)
```

Updates the weights of the portfolio in place. Returns the period portfolio return.

The portfolio is allowed to contain only a subset of the supplied asset returns, but not the other way around.

***Example***

```
w = [0.5, 0.25, 0.25]
r = [0.1, 0.1, -0.1]
FP = FinancialPortfolio(w)
update!(FP,r)
FP
```
