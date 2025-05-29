```
FluxFunction(func; parameters=nothing, top_temperature_dependent=false)
```

空気-氷、空気-雪、または氷-水の界面を横切るフラックスを表す `FluxFunction` を返します。フラックスは、次のシグネチャを持つ `func` によって計算されます。

```julia
flux = func(i, j, grid, clock, top_temperature, model_fields)
```

`parameters` が `isnothing` の場合、または

```julia
flux = func(i, j, grid, clock, top_temperature, model_fields, parameters)
```

`!isnothing(parameters)` の場合。`func` が `top_temperature_dependent` の場合、トップ温度の診断解決中に再計算されます。
