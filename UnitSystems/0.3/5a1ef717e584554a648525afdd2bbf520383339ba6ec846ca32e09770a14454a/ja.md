```Julia
gray(U::UnitSystem) = energy(𝟏,U,Metric)/mass(𝟏,U,Metric)
```

放射線のメートル法単位 (Gy または m²⋅s⁻²)。

```Julia
julia> gray(Metric) # Gy
1.0
```
