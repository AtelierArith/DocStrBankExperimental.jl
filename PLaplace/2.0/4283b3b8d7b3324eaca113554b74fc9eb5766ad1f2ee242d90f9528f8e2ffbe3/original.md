```
compute_derivative(
    D::AbstractDict{Tuple{Int64,Int64},SparseMatrixCSC{Float64,Int64}},
    v::AbstractVector{Float64}
) -> Dict{Tuple{Int64, Int64}, AbstractVector{Float64}}
```

Returs coefficient vectors of all the first partial derivatives $D^{(j,r)}v$ of a function given as coefficient vector v using the discrete derivative tensor D. Each key tuple (j,r) represents the derivative of the component r in direction x_j.
