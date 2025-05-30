```
function ∇(UD::AbstractUserDataType; quadorder = UD.quadorder - 1) -> DataFunction
```

同じ依存関係を持つDataFunctionを提供し、DataFunction UDの勾配を評価します。導関数はForwardDiffによって計算されます。
