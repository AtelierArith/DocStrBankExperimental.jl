```
dl2cl(dl::AbstractVector{T}, lmin::Integer) where {T <: Real}
```

Convert a set of $D_{\ell}$ to $C_{\ell}$ power spectrum, where $C_{\ell} = 2\pi D_{\ell} / \ell (\ell + 1)$. The first components are set to zero if not present. The monopole component is set to zero in any case to avoid Inf values.

# Arguments:

  * `dl::AbstractVector{T}` : Array of D_ℓ components
  * `lmin::Integer` : minimum l in the representation of the Dℓ power spectrum

# Returns:

  * `Vector{T}` : Array of C_ℓ power spectrum components
