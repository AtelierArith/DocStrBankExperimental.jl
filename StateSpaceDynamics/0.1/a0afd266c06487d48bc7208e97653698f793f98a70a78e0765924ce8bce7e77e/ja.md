```
fit!(model::ProbabilisticPCA, X::Matrix{<:AbstractFloat}, max_iter::Int=100, tol::AbstractFloat=1e-6)
```

EMアルゴリズムを使用してデータにPPCAモデルをフィットさせます。

# 引数:

  * `model::ProbabilisticPCA`: PPCAモデル
  * `X::Matrix{<:AbstractFloat}`: データ行列
  * `max_iter::Int`: 最大反復回数
  * `tol::AbstractFloat`: 収束のための許容誤差

# 例:

```julia
ppca = ProbabilisticPCA(K=1, D=2)
fit!(ppca, rand(10, 2))
```
