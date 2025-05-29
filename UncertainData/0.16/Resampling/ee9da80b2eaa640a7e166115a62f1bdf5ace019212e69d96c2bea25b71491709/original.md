```
resample(f::Function, x::UVAL_COLLECTION_TYPES, y::UVAL_COLLECTION_TYPES, n::Int, args...; kwargs...)
```

Resample the elements of `x` according to their furnishing uncertain values, yielding a length-`l` realisation of `x` if `length(x) = l`. Then, do the same for `y`. The elements of `x` and `y` are resampled independently, assuming no sequential dependence  between the elements of neither `x` nor `y`. 

Then, call `f(x_draw, y_draw, args..., kwargs...)` on the length-`l` samples  `x_draw` and `y_draw`. This process is repeated `n` times, yielding a length-`n`  distribution of evaluations of `f`.
