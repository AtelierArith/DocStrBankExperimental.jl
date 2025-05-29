```
FinancialPortfolio
```

ポートフォリオウェイトの（名前付きの可能性がある）コレクションです。ウェイトは、資産識別子とウェイトを一致させる辞書のようなオブジェクトであるか、単にウェイトのベクトルであることができます。

***例***

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
