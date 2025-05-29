```
NewtonResult
```

[`newton`](@ref)によって返される結果。

## フィールド

  * `return_code::Symbol`: `:success`、`:rejected`、または `:max_iters` のいずれか。
  * `x::Vector{ComplexF64}`: 得られた最後の値。
  * `accuracy::Float64`: `x` が真のゼロからの絶対距離の推定値。
  * `iters::Int` 実行された反復の数。
  * `contraction_ratio::Float64`: 値 `|xᵢ - xᵢ₋₁| / |xᵢ₋₁ - xᵢ₋₂|`。
