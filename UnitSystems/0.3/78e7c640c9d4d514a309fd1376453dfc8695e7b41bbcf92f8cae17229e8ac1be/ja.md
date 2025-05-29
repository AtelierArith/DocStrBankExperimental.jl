```Julia
electricalhorsepower(U::UnitSystem) = power(746,U,Metric)
```

アメリカ合衆国における電動モーターの`power`の単位。

```Julia
julia> electricalhorsepower(British) # lb⋅ft⋅s⁻¹
550.22136336084

julia> electricalhorsepower(Metric) # W
746

julia> electricalhorsepower(Engineering) # kgf⋅m⋅s⁻¹
76.07082948815345
```
