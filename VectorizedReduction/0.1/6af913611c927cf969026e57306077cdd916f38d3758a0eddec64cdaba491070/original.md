```
vlogsumexp(A::AbstractArray, dims)
```

Compute the log of the sum of exponentials of each element of `A` along the dimensions `dims`, which may be `::Int`, `::NTuple{M, Int} where {M}` or `::Colon`. Avoids overflow/underflow, but `+Inf` and `NaN` are not handled.
