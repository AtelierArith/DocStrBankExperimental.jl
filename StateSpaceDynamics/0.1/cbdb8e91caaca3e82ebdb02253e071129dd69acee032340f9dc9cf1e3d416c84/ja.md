```
sample(lds::LinearDynamicalSystem{S,O}, T_steps::Int, n_trials::Int) where {T<:Real, S<:GaussianStateModel{T}, O<:PoissonObservationModel{T}}
```

ポアソン線形動的システム (LDS) モデルから複数の試行のサンプルを取得します。

# 引数

  * `lds::LinearDynamicalSystem{S,O}`: 線形動的システムモデル。
  * `T_steps::Int`: 各試行のサンプルを取得する時間ステップの数。
  * `n_trials::Int`: サンプルを取得する試行の数。

# 戻り値

  * `x::Array{T, 3}`: 潜在状態変数。次元: (latent*dim, T*Steps, n_trials)
  * `y::Array{Int, 3}`: 観測データ。次元: (obs*dim, T*steps, n_trials)

# 例

```julia
lds = LinearDynamicalSystem(obs_dim=4, latent_dim=3)
x, y = sample(lds, 100, 10)  # 10試行、各100時間ステップ
```
