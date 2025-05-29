```
acwptall(x, wt[, L])
```

Computes the autocorrelation wavelet packet transform (ACWPT) on each slice of signal.

# Arguments

  * `x::AbstractArray{T} where T<:Number`: Input `N-1`-D signals, where each signal is sliced at dimension `N`.
  * `wt::OrthoFilter`: Orthogonal wavelet filter.
  * `L::Integer`: (Default: `minimum(size(xw)[1:end-1]) |> maxtransformlevels`) Number of levels of wavelet transforms.

# Returns

  * `::Array{T}`: Slices of transformed signals.

# Examples

```julia
using Wavelets, WaveletsExt

# Generate random signals
x = randn(32, 5)
# Create wavelet
wt = wavelet(WT.db4)

# ACWPT on all signals in x
xw = acwptall(x, wt)
```

**See also:** [`acwpt`](@ref)
