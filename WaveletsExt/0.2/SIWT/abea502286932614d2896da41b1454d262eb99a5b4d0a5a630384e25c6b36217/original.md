```
siwpd(x, wt[, L, d])
```

Computes the Shift-Invariant Wavelet Packet Decomposition originally developed by Cohen, Raz & Malah on the vector `x` using the discrete wavelet filter `wt` for `L` levels with depth `d`.

# Arguments

  * `x::AbstractVector{T} where T<:AbstractFloat`: 1D-signal.
  * `wt::OrthoFilter`: Wavelet filter.
  * `L::S where S<:Integer`: (Default: `maxtransformlevels(x)`) Number of transform levels.
  * `d::S where S<:Integer`: (Default: `L`) Depth of shifted transform for each node. Value of `d` must be strictly less than or equal to `L`.

# Returns

  * `ShiftInvariantWaveletTransformObject` containing node and tree details.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# SIWPD
siwpd(x, wt)        
siwpd(x, wt, 4)     # level 4 decomposition, where each decomposition has 4 levels of shifted decomposition.
siwpd(x, wt, 4, 2)  # level 4 decomposition, where each decomposition has 2 levels of shifted decomposition.
```

**See also:** [`isiwpd`](@ref), [`siwpd_subtree!`](@ref)
