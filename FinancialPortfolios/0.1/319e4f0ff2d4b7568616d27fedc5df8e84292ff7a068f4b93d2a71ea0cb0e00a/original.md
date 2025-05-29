```
portfolioreturn(fp::FinancialPortfolio,ret)
```

Compute the weighted portfolio return. If the portfolio weights have names or identifiers, the returns should as well. The portfolio is allowed to contain only a subset of the supplied asset returns, but not the other way around.

***Example***

```
w = [0.5, 0.25, 0.25]
r = [0.1, 0.1, -0.1]
FP = FinancialPortfolio(w)
portfolioreturn(FP,r)
```
