```
wpdall(x, wt[, L])
```

Computes the wavelet packet decomposition (WPD) on each slice of signal. Signals are sliced on the $n$-th dimension for an $n$-dimensional input `x`.

# Arguments

  * `x::AbstractArray{T} where T<:Number`: Input signals, where each slice corresponds to one signal. For a set of input signals `x` of dimension $n$, signals are sliced on the $n$-th dimension.
  * `wt::OrthoFilter`: Wavelet used.
  * `L::Integer`: (Default: `minimum(size(x)[1:end-1]) |> maxtransformlevels`) Number of levels of wavelet decomposition.

# Returns

`::Array{T}`: Array of decomposed signals. Signals are sliced by the final dimension.

# Examples

```julia
using Wavelets, WaveletsExt

# Generate random signals
x = randn(32, 5)
# Create wavelet
wt = wavelet(WT.db4)

# WPT on all signals in x
xw = wpdall(x, wt)
```

**See also:** [`wptall`](@ref), [`dwtall`](@ref), [`wpd`](@ref), [`wpd!`](@ref)
