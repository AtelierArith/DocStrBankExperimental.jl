```
nfct_get_coefficient_array(fhat::Vector{Float64},P::NFCT{D})::Array{Float64} where {D}
```

reshapes an coefficient vector returned from a linear map of the NFCT to an array.

# Input

  * `fhat` - the Fourier coefficients.
  * `P` - a NFCT plan structure.

# See also

[`NFCT{D}`](@ref), [`nfct_get_LinearMap`](@ref)
