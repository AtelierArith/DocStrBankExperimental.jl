```
q_vap_saturation(param_set, T, ρ, phase_type[, q::PhasePartition])
```

飽和比湿を計算します。与えられるものは次の通りです。

  * `param_set`: `AbstractParameterSet`、詳細については[`Thermodynamics`](@ref)を参照してください
  * `T`: 温度
  * `ρ`: 空気密度
  * `phase_type`: 熱力学的状態のタイプ
  * （オプション）`q`: [`PhasePartition`](@ref)

`PhasePartition` `q` が与えられた場合、飽和比湿は液体と氷の混合物のものであり、それぞれの相転移の潜熱の加重平均から熱力学的に一貫した方法で計算されます（Pressel et al., JAMES, 2015）。つまり、飽和蒸気圧とそれに基づく飽和比湿は、蒸発と昇華の潜熱の加重平均から計算され、重みは凝縮物の割合 `q.liq/(q.liq + q.ice)` と `q.ice/(q.liq + q.ice)` によって与えられます。

`PhasePartition` `q` が与えられない場合、または液体と氷の比湿がゼロの場合、飽和比湿は液体と氷の混合物のものであり、液体の割合は温度依存の `liquid_fraction(param_set, T, phase_type)` によって与えられ、氷の割合は補数 `1 - liquid_fraction(param_set, T, phase_type)` によって与えられます。
