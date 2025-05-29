```
function eval_div(UD::AbstractUserDataType) -> Function
```

データ関数 UD の x における発散を評価して返す関数を提供します（UD が時間に依存する場合は t も）。導関数は ForwardDiff によって計算されます。
