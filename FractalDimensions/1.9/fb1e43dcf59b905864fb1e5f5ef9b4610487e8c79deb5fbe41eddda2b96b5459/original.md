```
fixedmass_correlation_dim(X [, max_j]; kwargs...)
```

Use the fixed mass algorithm for computing the correlation sum, and use the result to compute the correlation dimension `Δ_M` of `X`.

This function does something extremely simple:

```julia
rs, ys = fixedmass_correlationsum(X, args...; kwargs...)
slopefit(rs, ys)[1]
```
