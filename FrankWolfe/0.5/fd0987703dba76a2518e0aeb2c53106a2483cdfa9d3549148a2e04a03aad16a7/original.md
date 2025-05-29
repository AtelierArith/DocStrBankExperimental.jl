```
compute_extreme_point(lmo::LinearMinimizationOracle, direction; kwargs...)
```

Computes the point `argmin_{v ∈ C} v ⋅ direction` with `C` the set represented by the LMO. Most LMOs feature `v` as a keyword argument that allows for an in-place computation whenever `v` is dense. All LMOs should accept keyword arguments that they can ignore.
