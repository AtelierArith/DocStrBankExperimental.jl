```
nfmt_get_coefficient_array(fhat::Vector{ComplexF64},P::NFMT{D})::Array{ComplexF64} where {D}
```

reshapes an coefficient vector returned from a linear map of the NFMT to an array.

# Input

  * `fhat` - the Fourier coefficients.
  * `P` - a NFMT plan structure.

# See also

[`NFMT{D}`](@ref), [`nfmt_get_LinearMap`](@ref)
