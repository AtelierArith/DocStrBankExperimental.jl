```
checkupdate!(fp::FinancialPortfolio,ret)
```

Updates the weights of the portfolio in place. Returns the period portfolio return.

If `ret` does not contain an entry for one of the existing portfolio positions, this function assumes the position was closed.

`positions` must be an object like `Dict` or `Dictionaries.AbstractDictionary`.

***Example***

```
w = Dict(["stockA"=>0.8,"stockB"=>0.2])
r = Dict(["stockA"=>0.1])
FP = FinancialPortfolio(w)
checkupdate!(FP,r)
FP
```
