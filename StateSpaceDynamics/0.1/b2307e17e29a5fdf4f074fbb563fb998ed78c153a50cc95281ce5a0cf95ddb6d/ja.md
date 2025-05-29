```
loglikelihood(model::ProbabilisticPCA, X::Matrix{<:AbstractFloat})
```

PPCAモデルに与えられたデータの対数尤度を計算します。

# 引数:

  * `model::ProbabilisticPCA`: PPCAモデル
  * `X::Matrix{<:AbstractFloat}`: データ行列

# 例:

```julia
ppca = ProbabilisticPCA(K=1, D=2)
loglikelihood(ppca, rand(10, 2))
```
