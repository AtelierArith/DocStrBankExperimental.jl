```
isdwtall(xw[, wt])
isdwtall(xw, wt, sm)
```

Computes the inverse stationary discrete wavelet transform (ISDWT) on each slice of signal.

# Arguments

  * `xw::AbstractArray{T} where T<:Number`: SDWT-transformed signal.
  * `wt::OrthoFilter`: (Default: `nothing`) Orthogonal wavelet filter.
  * `sm::Integer`: If `sm` is included as an argument, the `sm`-shifted inverse transform will be computed. This results in significantly faster computation, but fails to fully utilize the strength of redundant wavelet transforms.

# Returns

  * `::Array{T}`: Slices of reconstructed signals.

# Examples

```julia
using Wavelets, WaveletsExt

# Generate random signals
x = randn(32, 5)
# Create wavelet
wt = wavelet(WT.db4)

# SDWT on all signals in x
xw = sdwtall(x, wt)

# ISDWT on all signals in xw
x̂ = isdwtall(xw)
```

**See also:** [`isdwt`](@ref)
