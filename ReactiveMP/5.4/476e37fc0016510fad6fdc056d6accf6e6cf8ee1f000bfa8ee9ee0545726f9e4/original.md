```
diageye(::Type{T}, n::Int)
```

An alias for the `Matrix{T}(I, n, n)`. Returns a matrix of size `n x n` with ones (of type `T`) on the diagonal and zeros everywhere else.
