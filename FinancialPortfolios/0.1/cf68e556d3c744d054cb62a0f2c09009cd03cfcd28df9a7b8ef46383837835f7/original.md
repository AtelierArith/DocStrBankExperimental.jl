```
FinancialPortfolio
```

A (possibly named) collection of portfolio weights. Weights can be a dictionary-like object matching asset identifiers with weights or just a vector of weights.

***Example***

```
w = [0.5, 0.25, 0.25]
FP_vec = FinancialPortfolio(w)

nm = ["a", "b", "c"]
plain_dict = Dict(Iterators.zip(nm,w))
FP_plaindict = FinancialPortfolio(plain_dict)

using Dictionaries
fancy_dict = dictionary(plain_dict)
FP_fancydict = FinancialPortfolio(fancy_dict)
```
