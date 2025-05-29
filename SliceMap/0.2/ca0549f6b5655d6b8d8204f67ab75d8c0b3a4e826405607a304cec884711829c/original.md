```
slicemap(f, A; dims) ≈ mapslices(f, A; dims)
```

Like `mapcols()`, but for any slice. The function `f` must preserve shape, e.g. if `dims=(2,4)` then `f` must map matrices to matrices.

The gradient is for Zygote only.

Parameters within the function `f` (if there are any) should be correctly tracked, which is not the case for `mapcols()`. Keyword `rev=true` will apply `f` to `Iterators.reverse(Slices(A,...))`, thus iterating in the opposite order.
