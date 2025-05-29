```
liquid_fraction(param_set, T, phase_type[, q])
```

凝縮物の液体の割合は次のようになります。

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください。
  * `phase_type` は熱力学的状態のタイプです。

# PhaseNonEquil の動作

`q.liq` または `q.ice` がゼロでない場合、液体の割合はそれらから計算されます。

# ThermodynamicState

そうでない場合、相平衡が仮定され、液体の割合は `T_freeze` 以上で 1 であり、`T_icenuc` 以下でゼロに減少します。
