```
extrapolate!(fh::AbstractVector; power=1, atol=0, rtol=0, maxeval=typemax(Int), breaktol=Inf)
```

Similar to `extrapolate(fh)`, performs Richardson extrapolation on an array `fh` of `(f(h), h)` tuples (in order of decreasing `|h|`), but overwrites the array `fh` in-place with intermediate calculations.

(Thus, the array `fh` must be a vector of `Tuple{T,H}` values, where `H<:Number` is the type of `h` and `T` is the type of the extrapolated `f(0)` **result**.  This `T` should be a floating-point type, i.e. `fh` should contain `float(f(h))` if the function you are extrapolating is not already floating-point-valued.)
