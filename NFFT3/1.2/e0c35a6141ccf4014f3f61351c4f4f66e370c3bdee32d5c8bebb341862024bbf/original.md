```
nfft_get_coefficient_vector(fhat::Array{ComplexF64})::Vector{ComplexF64}
```

reshapes an coefficient array to an vector for multiplication with the linear map of the NFFT.

# Input

  * `fhat` - the Fourier coefficients.

# See also

[`NFFT{D}`](@ref), [`nfft_get_LinearMap`](@ref)
