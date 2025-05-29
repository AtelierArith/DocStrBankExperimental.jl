```
air_temperature(param_set, p::FT, θ::FT, Φ::FT, ::DryAdiabaticProcess)
```

等エントロピー過程における空気温度は、次のように定義されます。

  * `param_set` は `AbstractParameterSet` であり、詳細については [`Thermodynamics`](@ref) を参照してください
  * `p` は圧力
  * `θ` はポテンシャル温度
