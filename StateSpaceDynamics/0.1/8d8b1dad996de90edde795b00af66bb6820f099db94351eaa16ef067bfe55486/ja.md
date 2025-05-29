```
smooth(lds::LinearDynamicalSystem{S,O}, y::Array{T,3}) where {T<:Real, S<:GaussianStateModel{T}, O<:GaussianObservationModel{T}}
```

この関数は、システムパラメータと複数の試行に対する観測データを考慮して、線形動的システム（LDS）の直接スムージングを実行します。

# 引数

  * `lds::LinearDynamicalSystem{S,O}`: システムパラメータを表すLDSオブジェクト。
  * `y::Array{T,3}`: 次元が(obs*dim, tiem*steps, n_trials)の観測データ配列。

# 戻り値

  * `x::Array{T,3}`: 次元が(n*trials, time*steps, latent_dim)の最適状態推定。
  * `p_smooth::Array{T,4}`: 次元が(latent*dim, latent*dim, time*steps, n*trials)の事後共分散行列。
  * `inverse_offdiag::Array{T,4}`: 次元が(latent*dim, latent*dim, time*steps, n*trials)の逆オフダイアゴナル行列。

# 例

```julia
lds = GaussianLDS(obs_dim=4, latent_dim=3)
y = randn(5, 100, 4)  # 5試行、100時間ステップ、4観測次元
x, p_smooth, inverse_offdiag = smooth(lds, y)
```
