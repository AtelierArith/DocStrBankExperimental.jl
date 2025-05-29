```
resample(f::Function, x::UVAL_COLLECTION_TYPES, n::Int, args...; kwargs...)
```

Resample the elements of `x` according to their furnishing uncertain values, yielding a length-`l` realisation of `x` if `length(x) = l`. The elements of `x` are resampled  independently, assuming no sequential dependence between the elements. Then, call  `f(x, args...; kwargs...)` on the length-`l` sample with the given `args` and `kwargs`.  This process is repeated `n` times, yielding a length-`n` distribution of evaluations  of `f`.
