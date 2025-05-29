```Julia
horsepowermetric(U::UnitSystem) = power(𝟑*𝟓^2,U,Gravitational)
```

Unit of `power` derived from raising 75 kp by 1 m in 1  in 1 s.

```Julia
julia> horsepowermetric(British) # lb⋅ft⋅s⁻¹
542.4760388407421

julia> horsepowermetric(Metric) # W
735.49875

julia> horsepowermetric(Engineering) # kgf⋅m⋅s⁻¹
75
```
