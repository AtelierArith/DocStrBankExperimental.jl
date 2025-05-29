```
PoissonRegressionEmission
```

ポアソン回帰モデル。

# フィールド

  * `input_dim::Int`: 入力データの次元。
  * `include_intercept::Bool = true`: 切片項を含めるかどうか。
  * `β::Vector{<:Real} = if include_intercept zeros(input_dim + 1) else zeros(input_dim) end`: モデルの係数。最初の要素は、含まれている場合の切片項。
  * `λ::Float64 = 0.0`: 正則化パラメータ。
