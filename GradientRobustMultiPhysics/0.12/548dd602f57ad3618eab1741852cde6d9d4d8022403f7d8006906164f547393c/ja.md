```
function eval_curl(UD::AbstractUserDataType) -> Function
```

データ関数 UD の x におけるカールを評価して返す関数を提供します（UD が時間に依存する場合は t も）。返されるカールの種類は argsizes[1] に依存します。argsizes[1] = 1 の場合、2D のスカラー値関数のカールが計算され、argsizes[1] = 2 の場合は 2D のベクトル場のカールが計算され、argsizes[1] = 3 の場合は 3D のカールが計算されます。導関数は ForwardDiff によって計算されます。
