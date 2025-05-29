```
filt!(out, b, a, x, [si])
```

Same as [`filt`](@ref) but writes the result into the `out` argument, which may alias the input `x` to modify it in-place.
