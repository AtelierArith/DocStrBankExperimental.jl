```
LowRankGaussian(μ, D, U)
```

対角行列と低ランク共分散行列を持つガウス変分近似を構築します。

# 引数

  * `μ::AbstractVector{T}`: ガウスの平均。
  * `D::Vector{T}`: スケールの対角成分。
  * `U::Matrix{T}`: スケールの低ランク因子で、`size(U,2)` はランクです。
