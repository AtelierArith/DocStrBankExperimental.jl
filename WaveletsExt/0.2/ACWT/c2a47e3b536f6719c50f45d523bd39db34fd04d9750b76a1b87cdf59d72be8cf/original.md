```
acwpdall(x, wt[, L])
```

Computes the autocorrelation wavelet packet decomposition (ACWPD) on each slice of signal.

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

# ACWPD on all signals in x
xw = acwpdall(x, wt)
```

**See also:** [`acwpd`](@ref)
