```
D_prep(ℓₘₐₓ, [T=Float64])
```

Construct storage space and pre-compute recursion coefficients to compute Wigner's $\mathfrak{D}$ matrix in place.

This returns the `D_storage` arguments needed by [`D_matrices!`](@ref).
