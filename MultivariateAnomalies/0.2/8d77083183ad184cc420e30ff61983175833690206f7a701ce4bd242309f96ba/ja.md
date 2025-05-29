```
init_MedianCycle(dat::Array{tp}, cycle_length::Int = 46)
init_MedianCycle(temporal_length::Int[, cycle_length::Int = 46])
```

は、`get*MedianCycle!()`の入力として使用されるinit*MCオブジェクトを初期化します。入力は、サンプルデータまたは期待される入力ベクトルの時間的長さと年間サイクルの長さ（プリセット：`cycle_length = 46`）のいずれかです。
