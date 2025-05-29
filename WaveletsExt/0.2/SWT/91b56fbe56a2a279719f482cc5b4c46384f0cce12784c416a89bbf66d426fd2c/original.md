```
iswptall(xw[, wt])
iswptall(xw, wt, sm)
```

Computes the inverse stationary wavelet packet transform (ISWPT) on each slice of signal.

# Arguments

  * `xw::AbstractArray{T} where T<:Number`: SWPT-transformed signal.
  * `wt::Union{OrthoFilter, Nothing}`: (Default: `nothing`) Orthogonal wavelet filter.
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

# SWPT on all signals in x
xw = swptall(x, wt)

# ISWPT on all signals in xw
x̂ = iswptall(xw)
```

**See also:** [`iswpt`](@ref)
