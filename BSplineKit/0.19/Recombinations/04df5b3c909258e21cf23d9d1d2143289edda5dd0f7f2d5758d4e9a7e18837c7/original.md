```
recombination_matrix(R::AbstractBSplineBasis)
```

Get [`RecombineMatrix`](@ref) associated to the recombined basis.

For non-recombined bases such as [`BSplineBasis`](@ref), this returns the identity matrix (`LinearAlgebra.I`).
