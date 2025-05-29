```
dropagg(f, A::ClimArray, d [, W])
```

Apply statistics/aggregating function `f` (e.g. `sum` or `mean`) on array `A` across dimension(s) `d` and drop the corresponding dimension(s) from the result (Julia inherently keeps singleton dimensions).

If `A` is one dimensional, `dropagg` will return the single number of applying `f(A)`.

Optionally you can provide statistical weights in the form of a `W::ClimArray`. `W` must either have same size as `A` or have only one dimension and satisfy `length(W) == length(dims(A, d))` (i.e., a weight for each value of the dimension `d`). The latter case can only work when `d` is a single dimension. See also [`missing_weights`](@ref) for (properly) dealing with data that have `missing` values.
