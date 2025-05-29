```
LiquidIcePotTempSHumEquil(θ_liq_ice, ρ, q_tot)
```

[`PhaseEquil`](@ref) 熱力学状態を次の値から構築します：

  * `θ_liq_ice` 液体-氷のポテンシャル温度
  * `ρ` （湿った）空気の密度
  * `q_tot` 総特定湿度
  * `tol` 飽和調整のための許容誤差
  * `maxiter` 飽和調整のための最大反復回数
