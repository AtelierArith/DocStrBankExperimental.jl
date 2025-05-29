```
iacwptall(xw[, wt])
```

Computes the inverse autocorrelation wavelet packet transform (IACWPT) on each slice of signal.

# Arguments

  * `xw::AbstractArray{T} where T<:Number`: ACWPT-transformed signal.
  * `wt::Union{OrthoFilter, Nothing}`: (Default: `nothing`) Orthogonal wavelet filter.

# Returns

  * `::Array{T}`: Slices of reconstructed signals.

# Examples

```julia
using Wavelets, WaveletsExt

# Generate random signals
x = randn(32, 5)
# Create wavelet
wt = wavelet(WT.db4)

# ACWPT on all signals in x
xw = acwptall(x, wt)

# IACWPT on all signals in xw
x̂ = iacwptall(xw)
```

**See also:** [`iacwpt`](@ref)
