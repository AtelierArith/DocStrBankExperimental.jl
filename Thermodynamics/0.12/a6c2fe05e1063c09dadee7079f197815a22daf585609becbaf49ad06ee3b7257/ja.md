```
moist_static_energy(param_set, ts, e_pot)
```

湿潤静的エネルギーは、次のように与えられます。

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください
  * `ts` は熱力学的状態
  * `e_pot` は単位質量あたりのポテンシャルエネルギー（例：重力）
