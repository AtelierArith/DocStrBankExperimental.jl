```
finestdetailrange(x, tree[, redundant])
finestdetailrange(n, tree[, redundant])
```

Given a binary tree, returns the index range of the finest detail coefficients.

# Arguments

  * `x::AbstractArray{T} where T<:Number`: Decomposed 1D-signal.
  * `n::Integer`: Length of signal of interest.
  * `tree::BitVector`: Binary tree.
  * `redundant::Bool`: (Default: `false`) Whether the wavelet decomposition is redundant. Examples of redundant wavelet transforms are the Autocorrelation wavelet transform (ACWT), Stationary wavelet transform (SWT), and the Maximal Overlap wavelet transform (MOWT).

# Returns

`UnitRange{Integer}` or `::Tuple{UnitRange{Integer}, Integer}`: The index range of the finest detail subspace based on the input binary tree.

# Examples

```@repl
using Wavelets, WaveletsExt

x = randn(8)
wt = wavelet(WT.haar)
tree = maketree(x)

# Non-redundant wavelet transform
xw = wpd(x, wt)
finestdetailrange(xw, tree)          # 8:8

# Redundant wavelet transform
xw = swpd(x, wt)
finestdetailrange(xw, tree, true)    # (1:8, 15)
```

*See also:* [`coarsestscalingrange`](@ref)
