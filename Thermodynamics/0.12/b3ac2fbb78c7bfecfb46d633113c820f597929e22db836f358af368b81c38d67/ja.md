```
saturation_vapor_pressure(param_set, T, Liquid())
```

平面液体表面上の飽和蒸気圧を返します

  * `T` 温度
  * `param_set` `AbstractParameterSet`、詳細については [`Thermodynamics`](@ref) を参照してください

    `saturation_vapor_pressure(param_set, T, Ice())`

平面氷表面上の飽和蒸気圧を返します

  * `T` 温度
  * `param_set` `AbstractParameterSet`、詳細については [`Thermodynamics`](@ref) を参照してください

    `saturation_vapor_pressure(param_set, T, LH_0, Δcp)`

クラウジウス・クラペイロン関係の積分によって平面表面上の飽和蒸気圧を計算します。

クラウジウス・クラペイロン関係

```
`dlog(p_v_sat)/dT = [LH_0 + Δcp * (T-T_0)]/(R_v*T^2)`
```

は三重点温度 `T_triple` から積分され、キルヒホッフの関係を使用します

```
`L = LH_0 + Δcp * (T - T_0)`
```

相の定圧比熱が一定である特定の潜熱 `L` のために。温度 `T` に対する特定の潜熱の線形依存性により、クラウジウス・クラペイロン関係の解析的積分が可能になり、三重点圧力 `press_triple` の関数として飽和蒸気圧 `p_v_sat` を得ることができます。
