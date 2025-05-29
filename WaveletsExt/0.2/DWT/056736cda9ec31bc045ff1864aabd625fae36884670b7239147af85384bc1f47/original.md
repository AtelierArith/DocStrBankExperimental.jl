```
idwtall(xw, wt[, L])
```

Computes the inverse discrete wavelet transform (iDWT) on each slice of signal. Signals are sliced on the $n$-th dimension for an $n$-dimensional input `xw`.

!!! note
    `idwt` is currently available for 1-D, 2-D, and 3-D signals only.


# Arguments

  * `xw::AbstractArray{T} where T<:Number`: Input decomposed signals, where each slice corresponds to one signal. For a set of input signals `xw` of dimension $n$, signals are sliced on the $n$-th dimension.
  * `wt::OrthoFilter`: Wavelet used.
  * `L::Integer`: (Default: `Wavelets.maxtransformlevels(xwᵢ)`) Number of levels of wavelet transforms.

# Returns

`::Array{T}`: Slices of reconstructed signals. Signals are sliced the same way as the input `xw`.

# Examples

```julia
using Wavelets, WaveletsExt

# Generate random signals
x = randn(32, 5)
# Create wavelet
wt = wavelet(WT.db4)

# DWT on all signals in x
xw = dwtall(x, wt)

# iDWT on all signals
x̂ = idwtall(xw, wt)
```

**See also:** [`dwtall`](@ref), [`iwpdall`](@ref), [`iwptall`](@ref)
