```
FullRankGaussian(μ, L)
```

密な共分散行列を持つガウス変分近似を構築します。

# 引数

  * `μ::AbstractVector{T}`: ガウスの平均。
  * `L::LinearAlgebra.AbstractTriangular{T}`: ガウスの共分散のコレスキー因子。
