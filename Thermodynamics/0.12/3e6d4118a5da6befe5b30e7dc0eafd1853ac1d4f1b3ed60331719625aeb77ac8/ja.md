```
relative_humidity(param_set, T, p, phase_type, q::PhasePartition)
```

相対湿度（0と1の間にクリップされる）、次の条件で与えられます

  * `param_set` は `AbstractParameterSet` であり、詳細については [`Thermodynamics`](@ref) を参照してください
  * `p` は圧力
  * `phase_type` は熱力学的状態のタイプ

および、オプションで、

  * `q` は [`PhasePartition`](@ref) です。この引数がない場合、結果は乾燥空気に対するものです。

```
