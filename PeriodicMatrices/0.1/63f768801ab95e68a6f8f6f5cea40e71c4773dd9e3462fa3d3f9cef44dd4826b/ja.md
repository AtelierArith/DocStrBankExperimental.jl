```
pmrand(::Type{PM}, n::Int, m::Int[, period = 10]; ns = 1) 
pmrand(::Type{PM{:d,T}}, n::Int, m::Int[, period = 10]; ns = 1) 
pmrand(::Type{PM}, n::Vector{Int}, m::Vector{Int}[, period = 1]) 
pmrand(SwitchingPeriodicMatrix, n, m[, period = 10]; ns = [period]) 
pmrand(SwitchingPeriodicArray, n, m[, period = 10]; ns = [period])
```

タイプ `PM` または `PM{:d,T}` のランダムな `n×m` 離散時間周期行列を生成します。周期は `period`（デフォルト: `period = 10`）で、コンポーネント行列の数は `ns`（デフォルト: `ns = 1`）です。`PM = PeriodicMatrix` または `PM = PeriodicArray` の場合、`ns` はコンポーネント行列の数を指定します（デフォルト: `ns = 10`）。`PM = PeriodicMatrix` の場合、行列のコンポーネントの行と列の次元を含む2つの整数ベクトル `n` と `m` を使用して、時間変化する次元を持つ周期行列を指定できます。

`PM = SwitchingPeriodicMatrix` または `PM = SwitchingPeriodicArray` の場合、整数ベクトル `ns` はスイッチングの瞬間を指定します（デフォルト: `ns = [period]`）。行列要素のタイプ `T` は、例えば `PeriodicMatrix{:d,T}` を使用して指定でき、デフォルトでは `T = Float64` と仮定されます。
