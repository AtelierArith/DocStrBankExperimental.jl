```
deduce_limits(ysize, [ℓmin])
```

Deduce the value of `(ℓmin, ℓmax)` that produces $Y$ arrays of the given size.

If `ℓmin` is not given, it is assumed to be 0.  If it is set to `nothing`, the smallest possible value of `ℓmin` will be used.  However, note that this is not a well-posed problem; multiple combinations of `(ℓmin, ℓmax)` can give rise to $Y$ arrays of the same size.

See also [`Ysize`](@ref)
