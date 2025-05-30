```
d_prep(ℓₘₐₓ, [T=Float64])
```

Construct space and pre-compute recursion coefficients to compute Wigner's $d$ matrix in place.

This returns the `d_storage` arguments needed by [`d_matrices!`](@ref).
