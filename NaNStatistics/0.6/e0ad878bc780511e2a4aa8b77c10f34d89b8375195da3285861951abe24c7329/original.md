```julia
movsum(x::AbstractVecOrMat, n::Number)
```

Simple moving sum of `x` in 1 or 2 dimensions, spanning `n` bins (or n*n in 2D), returning an array of the same size as `x`.

For the resulting moving sum to be symmetric, `n` must be an odd integer; if `n` is not an odd integer, the first odd integer greater than `n` will be used instead.
