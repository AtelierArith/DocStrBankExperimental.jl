```
PhaseEquil_phq(param_set, p, h, q_tot[, maxiter, relative_temperature_tol, sat_adjust_method, T_guess])
```

温度から[`PhaseEquil`](@ref)熱力学状態を構築します。

  * `param_set`は`AbstractParameterSet`で、詳細は[`Thermodynamics`](@ref)を参照してください
  * `p`は圧力
  * `h`は比エンタルピー
  * `q_tot`は総比湿度
  * `T_guess`は飽和調整における温度の初期推定値です
