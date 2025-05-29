```
loglikelihood(x::Array{T, 3}, lds::LinearDynamicalSystem{S,O}, y::Array{T, 3}) where {T<:Real, S<:GaussianStateModel{T}, O<:PoissonObservationModel{T}}
```

ポアソン線形動的システムモデルの完全データ対数尤度を複数の試行に対して計算します。

# 引数

  * `x::Array{T, 3}`: 潜在状態変数。次元: (latent*dim, T*Steps, n_trials)
  * `lds::LinearDynamicalSystem{S,O}`: 線形動的システムモデル。
  * `y::Array{T, 3}`: 観測データ。次元: (obs*dim, T*steps, n_trials)

# 戻り値

  * `ll::T`: 対数尤度値。

# 例

```julia
lds = PoissonLDS(obs_dim=4, latent_dim=3)
x, y = sample(lds, 100, 10)  # 10試行、各100時間ステップ
ll = loglikelihood(x, lds, y)
```
