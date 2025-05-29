```
nfmt_get_coefficient_array(fhat::Vector{ComplexF64},N::Vector{Int64})::Array{ComplexF64}
```

reshapes an coefficient vector returned from a linear map of the NFMT to an array.

# Input

  * `fhat` - the Fourier coefficients.
  * `N` - the multibandlimit $(N_1, N_2, \ldots, N_D)$ of the trigonometric polynomial $f$.
  * `basis_vect` - tuple with the bases (`exp`, `cos`, `alg`) for each dimension

# See also

[`NFMT{D}`](@ref), [`nfmt_get_LinearMap`](@ref)
