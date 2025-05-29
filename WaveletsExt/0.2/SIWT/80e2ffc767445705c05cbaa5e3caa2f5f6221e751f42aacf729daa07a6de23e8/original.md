```
isiwpd(siwtObj)
```

Computes the Inverse Shift-Invariant Wavelet Packet Decomposition originally developed by Cohen, Raz & Malah.

# Arguments

  * `siwtObj::ShiftInvariantWaveletTransformObject{N,T₁,T₂} where {N,T₁<:Integer,T₂<:AbstractFloat`: SIWT object.

# Returns

  * `Vector{T₂}`: Reconstructed signal.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SIWPD
siwtObj = siwpd(x, wt)

# ISIWPD
isiwpd(siwtObj)
```

**See also:** [`siwpd`](@ref), [`isiwpd_subtree!`](@ref)
