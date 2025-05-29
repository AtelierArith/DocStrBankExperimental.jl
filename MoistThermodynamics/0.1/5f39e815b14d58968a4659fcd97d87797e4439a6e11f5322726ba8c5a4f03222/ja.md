```
LiquidIcePotTempSHumNonEquil(θ_liq_ice, ρ, q_pt)
```

[`PhaseNonEquil`](@ref) 熱力学状態を次の値から構築します：

  * `θ_liq_ice` 液体-氷のポテンシャル温度
  * `ρ` （湿った）空気の密度
  * `q_pt` 相の分配

および、オプションで

  * `tol` 非線形方程式解法のための許容誤差
  * `maxiter` 非線形方程式解法のための最大反復回数
