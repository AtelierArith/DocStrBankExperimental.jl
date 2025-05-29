```
nfct_get_coefficient_array(fhat::Vector{Float64},N::Vector{Int64})::Array{Float64}
```

reshapes an coefficient vector returned from a linear map of the NFCT to an array.

# Input

  * `fhat` - the Fourier coefficients.
  * `N` - the multibandlimit $(N_1, N_2, \ldots, N_D)$ of the trigonometric polynomial $f$.

# See also

[`NFCT{D}`](@ref), [`nfct_get_LinearMap`](@ref)
