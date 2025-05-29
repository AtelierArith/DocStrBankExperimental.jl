```
acwt(x, wt[, L=maxtransformlevels(x)])
```

Perform a forward ac wavelet transform of the array `x`. This method works for the 2D case as well. The wavelet type `wt` determines the transform type. Refer to Wavelet.jl for a list of available methods.

# Examples

```julia
acwt(x, wavelet(WT.db4))
```

**See also:** `iacwt`
