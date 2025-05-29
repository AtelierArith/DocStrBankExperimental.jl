```
checkupdate!(fp::FinancialPortfolio,ret)
```

ポートフォリオのウェイトをその場で更新します。期間ポートフォリオリターンを返します。

`ret` に既存のポートフォリオポジションのいずれかのエントリが含まれていない場合、この関数はそのポジションがクローズされたと仮定します。

`positions` は `Dict` または `Dictionaries.AbstractDictionary` のようなオブジェクトでなければなりません。

***例***

```
w = Dict(["stockA"=>0.8,"stockB"=>0.2])
r = Dict(["stockA"=>0.1])
FP = FinancialPortfolio(w)
checkupdate!(FP,r)
FP
```
