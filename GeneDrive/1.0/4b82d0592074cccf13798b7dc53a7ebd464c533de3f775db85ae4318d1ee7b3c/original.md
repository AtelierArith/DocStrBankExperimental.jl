```
mutable struct Density{D <: DensityDependence}
    model::Type{D}
    param::Float64
end
```

Data for density dependence model.

# Arguments

  * `model::Type{D}`: User-selected density dependence formulation. Includes `LogisticDensity`, `LinearDensity`, and `NoDensity`.
  * `param::Float64`: Calculated internally by `init` function.
