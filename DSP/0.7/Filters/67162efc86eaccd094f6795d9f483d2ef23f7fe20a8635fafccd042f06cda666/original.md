```
filt!(out, f, x[, si])
```

Same as [`filt()`](@ref) but writes the result into the `out` argument. Output array `out` may not be an alias of `x`, i.e. filtering may not be done in place.
