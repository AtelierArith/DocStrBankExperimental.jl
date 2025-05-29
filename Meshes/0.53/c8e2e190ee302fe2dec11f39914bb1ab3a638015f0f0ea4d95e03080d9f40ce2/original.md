```
RegularDiscretization(n1, n2, ..., np)
```

A method to discretize primitive geometries with `n1×n2×...×np` elements sampled regularly along each parametric dimensions. The adequate number of points is calculated for each type of geometry and passed to [`RegularSampling`](@ref).
