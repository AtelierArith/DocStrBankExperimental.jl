```
acwpt(x, wt[, L=maxtransformlevels(x)])
```

Perform a ac wavelet packet transform of the array `x`. The wavelet type `wt` determines the transform type.

# Examples

```julia
acwpt(x, wavelet(WT.db4))
```

**See also:** `iacwpt`
