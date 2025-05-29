```
cl2dl(cl::AbstractVector{T}, lmin::Integer) where {T <: Real}
```

Convert a set of $C_{\ell}$ to $D_{\ell}$ power spectrum, where $D_{\ell} = \ell (\ell + 1) C_{\ell} / 2\pi$. The first components are set to zero if not present.

# Arguments:

  * `cl::AbstractVector{T}` : Array of C_ℓ components
  * `lmin::Integer` : minimum l in the representation of the C_ℓ power spectrum

# Returns:

  * `Vector{T}` : Array of D_ℓ power spectrum components
