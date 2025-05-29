```
contrast(r1::RegDIDResultOrAgg, rs::RegDIDResultOrAgg...; kwargs)
```

[`ContrastResult`](@ref)を構築するには、各[`RegDIDResultOrAgg`](@ref)から計算された最小二乗重みを収集します。

# キーワード

  * `subset=nothing`: 含めるセルのインデックス（出力の行）。
  * `coefs=nothing`: 各結果から含める係数のインデックス（出力の列）。
