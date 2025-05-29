```
localreduce!(op, [dst = A,] A, dims, rngs; kwds...)
```

overwrites the contents of `dst` with the local reduction by the associative binary operator `op` of the values of `A` into contiguous hyper-rectangular neighborhoods defined by the interval(s) `rngs` along dimension(s) `dims` of `A`. Except if a single dimension of interest is specified by `dims`, the destination `dst` must have the same indices as the source `A` (that is, `axes(dst) == axes(A)`). Operation may be done in-place and `dst` and `A` can be the same; this is the default behavior if `dst` is not specified. The algorithm of van Herk-Gil-Werman is used to compute the reduction.

See [`localreduce`](@ref) for a full description of the method and for accepted keywords.

The in-place *morphological erosion* (local minimum) of the array `A` on a centered structuring element of width 7 in every dimension can be obtained by:

```
localreduce!(min, A, :, -3:3)
```
