```
saturation_vapor_pressure(T, Liquid())
```

温度 `T` における平面液体表面上の飽和蒸気圧を返します。

```
saturation_vapor_pressure(T, Ice())
```

温度 `T` における平面氷表面上の飽和蒸気圧を返します。

```
saturation_vapor_pressure(T, LH_0, Δcp)
```

Clausius-Clapeyron 関係の積分によって平面表面上の飽和蒸気圧を計算します。

Clausius-Clapeyron 関係

```
dlog(p_v_sat)/dT = [LH_0 + Δcp * (T-T_0)]/(R_v*T^2)
```

は三重点温度 `T_triple` から積分され、キルヒホッフの関係を使用します。

```
L = LH_0 + Δcp * (T - T_0)
```

相の定常比熱が一定であるときの特定の潜熱 `L` のために。潜熱が温度 `T` に線形依存することにより、Clausius-Clapeyron 関係の解析的積分が可能になり、三重点圧力 `press_triple` の関数として飽和蒸気圧 `p_v_sat` を得ることができます。
