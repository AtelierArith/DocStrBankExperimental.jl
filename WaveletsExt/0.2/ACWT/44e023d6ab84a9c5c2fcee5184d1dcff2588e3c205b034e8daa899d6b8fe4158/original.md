```
acwpd(x, wt[, L])
```

Performs a discrete autocorrelation wavelet packet transform for a given signal `x`. The wavelet type `wt` determines the transform type. Refer to Wavelet.jl for a list of available methods.

# Arguments

  * `x::AbstractArray{T} where T<:Number`: Original signal, preferably of size 2ᴷ or (2ᴷ,2ᴹ) where $K, M \in \mathbb{N}$.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `L::Integer`: (Default: `maxtransformlevels(x)`) Number of levels of decomposition.

# Returns

`::Array{T}`: Output from ACWPD on `x`.

# Examples

```julia
using Wavelets, WaveletsExt

# Setup
x = generatesignals(:heavysine)
wt = wavelet(WT.haar)

# ACWPD
acwpd(x, wt)

acwpd(x, wt, 4)
```

**See also:** [`iacwpd`](@ref), [`acdwt`](@ref), [`acdwt_step`](@ref)
