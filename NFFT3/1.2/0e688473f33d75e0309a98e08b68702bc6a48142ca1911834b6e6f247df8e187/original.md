```
nfft_get_coefficient_array(fhat::Vector{ComplexF64},P::NFFT{D})::Array{ComplexF64} where {D}
```

reshapes an coefficient vector returned from a linear map of the NFFT to an array.

# Input

  * `fhat` - the Fourier coefficients.
  * `P` - a NFFT plan structure.

# See also

[`NFFT{D}`](@ref), [`nfft_get_LinearMap`](@ref)
