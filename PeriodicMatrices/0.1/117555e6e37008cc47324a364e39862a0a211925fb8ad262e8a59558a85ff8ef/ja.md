```
pmrand([::Type{T},] m::Vector{Int},n::Vector{Int}[, period = 10])
```

周期 `period`（デフォルト: `period = 10`）を持つ `PeriodicMatrix` 型のランダム離散時間周期行列を生成します。コンポーネント行列の時間変動する行と列の次元は、それぞれ整数ベクトル `m` と `n` によって指定されます。`T` は行列要素の型で、指定しない場合はデフォルトで `T = Float64` となります。
