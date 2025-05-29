```Julia
boilerhorsepower(U::UnitSystem) = frequency(1339/𝟐^4/𝟑^2,U,Metric)*thermalunit(U)
```

Unit of `power` derived from evaporating 34.5 lb of boiling water in 1 hour.

```Julia
julia> boilerhorsepower(British) # lb⋅ft⋅s⁻¹
7235.785026428903

julia> boilerhorsepower(Metric) # W
9810.407209099903

julia> boilerhorsepower(Engineering) # kgf⋅m⋅s⁻¹
1000.3831287034719
```
