```
LiquidIcePotTempSHumEquil_given_pressure(θ_liq_ice, p, q_tot)
```

次の値から[`PhaseEquil`](@ref)熱力学状態を構築します：

  * `θ_liq_ice` 液体-氷のポテンシャル温度
  * `p` 圧力
  * `q_tot` 総比湿
  * `tol` 飽和調整のための許容誤差
  * `maxiter` 飽和調整のための最大反復回数
