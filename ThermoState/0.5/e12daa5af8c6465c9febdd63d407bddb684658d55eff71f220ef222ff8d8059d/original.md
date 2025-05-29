```
@to_units f(x)
```

return `f(x)` with Unitful units. the measurement unit is determined by `default_units(a::typeof(f))`

#example:

```julia-repl
julia> critical_pressure(water)
2.2064e7 Pa
```
