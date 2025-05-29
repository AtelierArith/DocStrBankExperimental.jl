```
iwpdall(xw, wt[, L; standard])
iwpdall(xw, wt, tree[; standard])
```

Computes the inverse wavelet packet decomposition (IWPD) on each slice of signal. Signals are sliced on the $n$-th dimension for an $n$-dimensional input `xw`.

# Arguments

  * `xw::AbstractArray{T} where T<:Number`: Input signals, where each slice corresponds to one signal decomposition. For a set of input signals `x` of dimension $n$, `xw` is sliced on the $n$-th dimension.
  * `wt::OrthoFilter`: Wavelet used.
  * `L::Integer`: (Default: `Wavelets.maxtransformlevels(xᵢ)`) Number of levels of wavelet decomposition.

# Keyword Arguments

  * `standard::Bool`: (Default: `true`) Whether to compute the standard or non-standard wavelet transform. Only applicable for 2D signals.

# Returns

`::Array{T}`: Array of decomposed signals. Signals are sliced by the final dimension.

# Examples

```julia
using Wavelets, WaveletsExt

# Generate random signals
x = randn(32, 5)
# Create wavelet
wt = wavelet(WT.db4)

# WPD on all signals in x
xw = wpdall(x, wt)

# IWPD on all signals
x̂ = iwpdall(xw, wt)
```

**See also:** [`wptall`](@ref), [`dwtall`](@ref), [`wpd`](@ref), [`wpd!`](@ref)
