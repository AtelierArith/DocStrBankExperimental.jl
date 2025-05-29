```
q_vap_from_RH_liquid(param_set, p, T, RH)
```

水の相対湿度から水蒸気の比湿を計算します（すなわち、氷の上の飽和蒸気圧は寒い温度でも考慮されません）。

入力:

  * `param_set` は `AbstractParameterSet` で、詳細は [`Thermodynamics`](@ref) を参照してください
  * `p` 圧力
  * `T` 温度
  * `RH` 相対湿度
