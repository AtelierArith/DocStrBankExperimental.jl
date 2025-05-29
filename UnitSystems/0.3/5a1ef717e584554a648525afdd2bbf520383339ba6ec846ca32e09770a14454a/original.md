```Julia
gray(U::UnitSystem) = energy(𝟏,U,Metric)/mass(𝟏,U,Metric)
```

Metric unit of radioactivity (Gy or m²⋅s⁻²).

```Julia
julia> gray(Metric) # Gy
1.0
```
