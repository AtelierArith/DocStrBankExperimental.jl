```julia
struct WLE{T<:Roots.AbstractSecantMethod} <: PersonParameters.PersonParameterAlgorithm
```

ウォームのアイテム応答モデルの人パラメータに対する加重尤度推定。

# 参考文献

  * Warm, T. A. (1989). アイテム応答理論における能力の加重尤度推定。Psychometrika, 54, 427-450. doi: 10.1007/BF02294627
