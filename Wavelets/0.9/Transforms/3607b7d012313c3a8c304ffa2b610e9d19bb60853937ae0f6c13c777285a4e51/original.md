```
dwt(x, wt[, L=maxtransformlevels(x)])
```

Perform a discrete wavelet transform of the array `x`. The wavelet type `wt` determines the transform type (filter or lifting) and the wavelet class, see `wavelet`.

The number of transformation levels `L` can be any non-negative integer such that the size of `x` is divisible by `L`. Performs the identity transformation if `L==0`.

# Examples

```julia
dwt(x, wavelet(WT.coif6))
```

**See also:** `idwt`, `dwt!`, `wavelet`
