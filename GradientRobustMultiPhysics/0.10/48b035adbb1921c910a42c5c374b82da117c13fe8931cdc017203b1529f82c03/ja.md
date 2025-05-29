```
function curl(UD::AbstractUserDataType; quadorder = UD.quadorder - 1)
```

同じ依存関係を持つDataFunctionを提供し、DataFunction UDのカールを評価します。導関数はForwardDiffによって計算されます。
