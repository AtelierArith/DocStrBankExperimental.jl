```
saturation_excess(param_set, T, ρ, phase_type, q::PhasePartition)
```

平衡状態における飽和過剰は次のように定義されます。

  * `param_set` は `AbstractParameterSet` で、詳細については [`Thermodynamics`](@ref) を参照してください
  * `T` は温度
  * `ρ` は（湿）空気の密度
  * `phase_type` は熱力学的状態のタイプ
  * `q` は [`PhasePartition`](@ref)

飽和過剰は、全体の比湿 `q.tot` と平衡状態における飽和比湿との違いであり、この違いが正である場合にのみ非ゼロと定義されます。
