```Julia
electricalhorsepower(U::UnitSystem) = power(746,U,Metric)
```

Unit of `power` for electrical motors in the United States.

```Julia
julia> electricalhorsepower(British) # lb⋅ft⋅s⁻¹
550.22136336084

julia> electricalhorsepower(Metric) # W
746

julia> electricalhorsepower(Engineering) # kgf⋅m⋅s⁻¹
76.07082948815345
```
