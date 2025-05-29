```Julia
fahrenheit(U::UnitSystem) = temperature(Constant(459.67),U,English)
```

英語の `temperature` 単位 (K または °R)。

```Julia
julia> fahrenheit(Metric) # K
255.37222222222226

julia> fahrenheit(SI2019) # K
255.3722221344396

julia> fahrenheit(British) # °R
459.67
```
