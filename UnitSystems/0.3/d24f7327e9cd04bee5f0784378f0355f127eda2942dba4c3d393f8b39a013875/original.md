```Julia
horsepower(U::UnitSystem) = power(𝟐*𝟓^2*𝟏𝟏,U,British)
```

Unit of `power` derived from raising 550 lb by 1 ft in 1  in 1 s.

```Julia
julia> horsepower(British) # lb⋅ft⋅s⁻¹
550

julia> horsepower(Metric) # W
745.6998715822704

julia> horsepower(Engineering) # kgf⋅m⋅s⁻¹
76.04022490680002
```
