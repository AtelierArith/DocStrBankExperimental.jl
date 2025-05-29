```
iacdwtall(xw[, wt])
```

Computes the inverse autocorrelation discrete wavelet transform (IACDWT) on each slice of signal.

# Arguments

  * `xw::AbstractArray{T} where T<:Number`: ACDWT-transformed signal.
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

# ACDWT on all signals in x
xw = acdwtall(x, wt)

# IACDWT on all signals in xw
x̂ = iacdwtall(xw)
```

**See also:** [`iacdwt`](@ref)
