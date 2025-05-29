```
nfst_get_coefficient_array(fhat::Vector{Float64},P::NFST{D})::Array{Float64} where {D}
```

reshapes an coefficient vector returned from a linear map of the NFST to an array.

# Input

  * `fhat` - the Fourier coefficients.
  * `P` - a NFST plan structure.

# See also

[`NFST{D}`](@ref), [`nfst_get_LinearMap`](@ref)
