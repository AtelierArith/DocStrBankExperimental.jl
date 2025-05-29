```
wptall(x, wt[, L])
wptall(x, wt, tree)
```

Computes the wavelet packet transform (WPT) on each slice of signal. Signals are sliced on the $n$-th dimension for an $n$-dimensional input `x`.

!!! note
    `wpt` is currently available for 1-D and 2-D signals only.


# Arguments

  * `x::AbstractArray{T} where T<:Number`: Input signals, where each slice corresponds to one signal. For a set of input signals `x` of dimension $n$, signals are sliced on the $n$-th dimension.
  * `wt::OrthoFilter`: Wavelet used.
  * `L::Integer`: (Default: `Wavelets.maxtransformlevels(xᵢ)`) Number of levels of wavelet decomposition.
  * `tree::BitVector`: (Default: `Wavelets.maketree(xᵢ, :full)`) Tree to follow for wavelet decomposition. Default value is only applicable for 1D signals.

# Returns

`::Array{T}`: Slices of transformed signals. Signals are sliced the same way as the input signal `x`.

# Examples

```julia
using Wavelets, WaveletsExt

# Generate random signals
x = randn(32, 5)
# Create wavelet
wt = wavelet(WT.db4)

# WPT on all signals in x
xw = wptall(x, wt)
```

**See also:** [`wpdall`](@ref), [`dwtall`](@ref), [`wpt`](@ref)
