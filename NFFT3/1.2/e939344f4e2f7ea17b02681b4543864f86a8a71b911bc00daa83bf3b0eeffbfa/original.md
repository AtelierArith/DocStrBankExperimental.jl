```
nfmt_get_coefficient_vector(fhat::Array{ComplexF64})::Vector{ComplexF64}
```

reshapes an coefficient array to an vector for multiplication with the linear map of the NFMT.

# Input

  * `fhat` - the Fourier coefficients.

# See also

[`NFMT{D}`](@ref), [`nfmt_get_LinearMap`](@ref)
