```
loglikelihood(x::Matrix{T}, lds::LinearDynamicalSystem{S,O}, y::Matrix{T}) where {T<:Real, S<:GaussianStateModel, O<:PoissonObservationModel}
```

ポアソン線形動的システムモデルの完全データ対数尤度を単一試行について計算します。

# 引数

  * `x::Matrix{T}`: 潜在状態変数。次元: (latent*dim, T*steps)
  * `lds::LinearDynamicalSystem{S,O}`: 線形動的システムモデル。
  * `y::Matrix{T}`: 観測データ。次元: (obs*dim, T*steps)
  * `w::Vector{T}`: 対数尤度計算における各観測の重み。現在は使用されていません。

# 戻り値

  * `ll::T`: 対数尤度値。

# 例

```juliaestep!
lds = PoissonLDS(obs_dim=4, latent_dim=3)
x, y = sample(lds, 100, 1)  # 1試行、100時間ステップ
ll = loglikelihood(x, lds, y)
```
