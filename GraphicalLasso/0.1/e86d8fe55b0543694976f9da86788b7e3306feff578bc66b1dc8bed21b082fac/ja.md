```
cdlasso(W11::Matrix{T}, s12::Vector{T}, λ::Real; max_iter::Int=100, tol::T=1e-5) where {T<:Real}
```

座標降下Lasso問題を解決します。

# 引数

  * `W11::Matrix{T}`: 座標降下更新に使用される正方行列。
  * `s12::Vector{T}`: 座標降下更新に使用されるベクトル。
  * `λ::Real`: 正則化パラメータ。
  * `max_iter::Int=100`: 最大反復回数。 (オプション)
  * `tol::T=1e-5`: 収束基準の許容誤差。 (オプション)

# 戻り値

  * `Vector{T}`: 解ベクトル `β`。
