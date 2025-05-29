```Julia
horsepowermetric(U::UnitSystem) = power(𝟑*𝟓^2,U,Gravitational)
```

`power`の単位は、75 kpを1 mの高さで1秒間に上げることから導出されます。

```Julia
julia> horsepowermetric(British) # lb⋅ft⋅s⁻¹
542.4760388407421

julia> horsepowermetric(Metric) # W
735.49875

julia> horsepowermetric(Engineering) # kgf⋅m⋅s⁻¹
75
```
