```
GaussianRegressionEmission
```

ガウス回帰エミッションモデル。

# フィールド

  * `input_dim::Int`: 入力データの次元。
  * `output_dim::Int`: 出力データの次元。
  * `include_intercept::Bool = true`: 切片項を含めるかどうか; trueの場合、βの最初の列は切片/バイアスであると仮定されます。
  * `β::Matrix{<:Real} = if include_intercept zeros(input_dim + 1, output_dim) else zeros(input_dim, output_dim) end`: モデルの係数行列。形状はinput*dim by output*dim。最初の行は、含まれている場合は切片項です。
  * `Σ::Matrix{<:Real} = Matrix{Float64}(I, output_dim, output_dim)`: モデルの共分散行列。
  * `λ::Float64 = 0.0`: 正則化パラメータ。
