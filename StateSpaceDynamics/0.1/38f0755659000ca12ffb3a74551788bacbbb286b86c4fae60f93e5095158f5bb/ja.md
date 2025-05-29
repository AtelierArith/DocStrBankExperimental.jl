```
GaussianMixtureModel
```

クラスタリングと密度推定のためのガウス混合モデル。

# フィールド

  * `k::Int`: クラスターの数。
  * `μₖ::Matrix{<:Real}`: 各クラスターの平均（次元：data_dim x k）。
  * `Σₖ::Array{Matrix{<:Real}, 1}`: 各クラスターの共分散行列。
  * `πₖ::Vector{Float64}`: 各クラスターの混合係数。

# 例

```julia
gmm = GaussianMixtureModel(3, 2) # 3つのクラスターと2次元データを持つガウス混合モデルを作成
fit!(gmm, data)
```
