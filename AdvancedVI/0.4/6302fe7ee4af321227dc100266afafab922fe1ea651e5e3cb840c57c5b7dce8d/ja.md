```
MeanFieldGaussian(μ, L)
```

対角共分散行列を持つガウス変分近似を構築します。

# 引数

  * `μ::AbstractVector{T}`: ガウスの平均。
  * `L::Diagonal{T}`: ガウスの共分散の対角コレスキー因子。
