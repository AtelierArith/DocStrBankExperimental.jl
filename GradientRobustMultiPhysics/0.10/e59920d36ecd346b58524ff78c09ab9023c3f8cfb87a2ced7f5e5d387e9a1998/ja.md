```
function Δ(UD::AbstractUserDataType; quadorder = UD.quadorder - 2)
```

同じ依存関係を持つDataFunctionを提供し、DataFunction UDのラプラシアンを評価します。導関数はForwardDiffによって計算されます。
