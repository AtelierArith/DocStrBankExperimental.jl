```Julia
curie(U::UnitSystem) = frequency(𝟏,U,Metric)
```

Reference unit of radioactivity (Bq or s⁻¹).

```Julia
julia> curie(Metric) # Bq
3.7e10

julia> curie(IAU) # D⁻¹
3.1968e15
```
