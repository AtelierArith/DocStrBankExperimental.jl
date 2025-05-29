```
GaussianLDS(; A, C, Q, R, x0, P0, fit_bool, obs_dim, latent_dim)
```

ガウス状態と観測モデルを持つ線形動的システムを構築します。

# 引数

  * `A::Matrix{T}=Matrix{T}(undef, 0, 0)`: 遷移行列
  * `C::Matrix{T}=Matrix{T}(undef, 0, 0)`: 観測行列
  * `Q::Matrix{T}=Matrix{T}(undef, 0, 0)`: プロセスノイズ共分散
  * `R::Matrix{T}=Matrix{T}(undef, 0, 0)`: 観測ノイズ共分散
  * `x0::Vector{T}=Vector{T}(undef, 0)`: 初期状態
  * `P0::Matrix{T}=Matrix{T}(undef, 0, 0)`: 初期状態共分散
  * `fit_bool::Vector{Bool}=fill(true, 6)`: 最適化中にフィットさせるパラメータを示すベクトル
  * `obs_dim::Int`: 観測の次元（CまたはRが提供されていない場合は必須）
  * `latent_dim::Int`: 潜在状態の次元（A、Q、x0、P0、またはCが提供されていない場合は必須）
