```
specific_entropy(param_set, p, T, q)
specific_entropy(param_set, ts)
```

特定エントロピーは、次のように与えられます。

  * `param_set` は `AbstractParameterSet` であり、詳細については [`Thermodynamics`](@ref) を参照してください。
  * `p` は圧力
  * `T` は温度
  * `q` は相分配

[Pressel2015](@cite) の式 (29)-(33) に従います。
