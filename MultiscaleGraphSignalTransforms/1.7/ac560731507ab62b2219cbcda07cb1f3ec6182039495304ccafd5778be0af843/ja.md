```
frame_approx(f, U, V; num_kept = length(f))
```

フレーム `U` によって信号 `f` を近似します。

# 入力引数

  * `f::Vector{Float64}`: 入力グラフ信号
  * `U::Matrix{Float64}`: フレーム演算子（行列または辞書）
  * `V::Matrix{Float64}`: `U` の双対フレーム演算子
  * `num_kept::Int64`: 保持する係数の数 (NCR)

# 出力引数

  * `rel_error::Vector{Float64}`: 相対誤差
  * `f_approx::Vector{Float64}`: 近似された信号
