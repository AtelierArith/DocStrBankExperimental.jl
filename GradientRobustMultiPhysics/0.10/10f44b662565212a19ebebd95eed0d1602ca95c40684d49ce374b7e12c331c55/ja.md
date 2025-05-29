```
function eval_∇(UD::AbstractUserDataType) -> Function
```

データ関数 UD のラプラス演算子を x で（および UD が時間に依存する場合は t で）評価して返す関数を提供します。導関数は ForwardDiff によって計算されます。
