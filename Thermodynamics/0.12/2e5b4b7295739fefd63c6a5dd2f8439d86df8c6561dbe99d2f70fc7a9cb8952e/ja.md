```
air_pressure(param_set, T::FT, T∞::FT, p∞::FT, ::DryAdiabaticProcess)
```

等エントロピー過程における空気圧は、次のように定義されます。

  * `param_set` は `AbstractParameterSet` であり、詳細については [`Thermodynamics`](@ref) を参照してください
  * `T` は温度
  * `T∞` は周囲温度
  * `p∞` は周囲圧力
