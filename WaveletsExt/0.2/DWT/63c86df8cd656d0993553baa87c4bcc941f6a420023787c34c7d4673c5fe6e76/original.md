```
dwtall(x, wt[, L])
```

Computes the discrete wavelet transform (DWT) on each slice of signal. Signals are sliced on the $n$-th dimension for an $n$-dimensional input `x`.

!!! note
    `dwt` is currently available for 1-D, 2-D, and 3-D signals only.


# Arguments

  * `x::AbstractArray{T} where T<:Number`: Input signals, where each slice corresponds to one signal. For a set of input signals `x` of dimension $n$, signals are sliced on the $n$-th dimension.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `L::Integer`: (Default: `Wavelets.maxtransformlevels(xᵢ)`) Number of levels of wavelet transforms.

# Returns

`::Array{T}`: Slices of transformed signals. Signals are sliced the same way as the input signal `x`.

# Examples

```julia
using Wavelets, WaveletsExt

# Generate random signals
x = randn(32, 5)
# Create wavelet
wt = wavelet(WT.db4)

# DWT on all signals in x
xw = dwtall(x, wt)
```

**See also:** [`idwtall`](@ref), [`wpdall`](@ref), [`wptall`](@ref)
