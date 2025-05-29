```
function H(UD::AbstractUserDataType; quadorder = UD.quadorder - 2) -> DataFunction
```

同じ依存関係を持つDataFunctionを提供し、DataFunction UDのヘッセ行列を評価します。導関数はForwardDiffによって計算されます。
