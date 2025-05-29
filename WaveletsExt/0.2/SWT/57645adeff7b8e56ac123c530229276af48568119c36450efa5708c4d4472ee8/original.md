```
swpdall(x, wt[, L])
```

Computes the stationary wavelet packet decomposition (SWPD) on each slice of signal.

# Arguments

  * `x::AbstractArray{T} where T<:Number`: Input `N-1`-D signals, where each signal is sliced at dimension `N`.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `L::Integer`: (Default: `Wavelets.maxtransformlevels(xᵢ)`) Number of levels of wavelet transforms.

# Returns

  * `::Array{T}`: Slices of transformed signals.

# Examples

```julia
using Wavelets, WaveletsExt

# Generate random signals
x = randn(32, 5)
# Create wavelet
wt = wavelet(WT.db4)

# SWPD on all signals in x
xw = swpdall(x, wt)
```

**See also:** [`swpd`](@ref)
