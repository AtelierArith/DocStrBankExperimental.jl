```
PoissonLDS(; A, C, Q, log_d, x0, P0, refractory_period, fit_bool, obs_dim, latent_dim)
```

ガウス状態とポアソン観測モデルを持つ線形動的システムを構築します。

# 引数

  * `A::Matrix{T}=Matrix{T}(undef, 0, 0)`: 遷移行列
  * `C::Matrix{T}=Matrix{T}(undef, 0, 0)`: 観測行列
  * `Q::Matrix{T}=Matrix{T}(undef, 0, 0)`: プロセスノイズ共分散
  * `log_d::Vector{T}=Vector{T}(undef, 0)`: 平均発火率ベクトル（対数空間）
  * `x0::Vector{T}=Vector{T}(undef, 0)`: 初期状態
  * `P0::Matrix{T}=Matrix{T}(undef, 0, 0)`: 初期状態共分散
  * `refractory_period::Int=1`: 不応期
  * `fit_bool::Vector{Bool}=fill(true, 7)`: 最適化中にフィットさせるパラメータを示すベクトル
  * `obs_dim::Int`: 観測の次元（C、D、またはlog_dが提供されていない場合は必須）
  * `latent_dim::Int`: 潜在状態の次元（A、Q、x0、P0、またはCが提供されていない場合は必須）
