```Julia
curie(U::UnitSystem) = frequency(𝟏,U,Metric)
```

放射能の基準単位（Bqまたはs⁻¹）。

```Julia
julia> curie(Metric) # Bq
3.7e10

julia> curie(IAU) # D⁻¹
3.1968e15
```
