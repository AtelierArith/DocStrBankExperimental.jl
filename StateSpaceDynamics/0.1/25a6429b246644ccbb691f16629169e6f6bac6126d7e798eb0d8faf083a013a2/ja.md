```
M_Step!(model::ProbabilisticPCA, X::Matrix{<:AbstractFloat}, E_z::Matrix{<:AbstractFloat}, E_zz::Array{<:AbstractFloat, 3}
```

PPCAのEMアルゴリズムの最大化ステップ。詳細についてはBishopのパターン認識と機械学習を参照してください。

# 引数:

  * `model::ProbabilisticPCA`: PPCAモデル
  * `X::Matrix{<:AbstractFloat}`: データ行列
  * `E_z::Matrix{<:AbstractFloat}`: E[z]
  * `E_zz::Matrix{<:AbstractFloat}`: E[zz']

# 例:

```julia
ppca = ProbabilisticPCA(K=1, D=2)
E_z, E_zz = E_Step(ppca, rand(10, 2))
M_Step!(ppca, rand(10, 2), E_z, E_zzᵀ)
```
