```
smooth(lds::LinearDynamicalSystem{S,O}, y::Matrix{T}) where {T<:Real, S<:GaussianStateModel{T}, O<:GaussianObservationModel{T}}
```

この関数は、システムパラメータと観測データが与えられた線形動的システム（LDS）に対して直接スムージングを行います。

# 引数

  * `lds::LinearDynamicalSystem{S,O}`: システムパラメータを表すLDSオブジェクト。
  * `y::Matrix{T}`: 観測データ行列。
  * `w::Vector{Float64}`: データに重みを付けるための係数。

# 戻り値

  * `x::Matrix{T}`: 最適な状態推定。
  * `p_smooth::Array{T, 3}`: 事後共分散行列。
  * `inverse_offdiag::Array{T, 3}`: 逆オフ対角行列。
  * `Q_val::T`: Q関数の値。

# 例

```julia
lds = GaussianLDS(obs_dim=4, latent_dim=3)
y = randn(100, 4)  # 100タイムステップ、4つの観測次元
x, p_smooth, inverse_offdiag, Q_val = DirectSmoother(lds, y)
```
