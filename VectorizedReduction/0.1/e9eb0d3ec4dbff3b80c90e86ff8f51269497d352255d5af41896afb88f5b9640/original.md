```
vtsoftmax(A::AbstractArray, dims)
```

Compute the softmax function, treating each slice of `A` specified by `dims` as if it were a single vector; `dims` may be `::Int`, `::NTuple{M, Int} where {M}` or `::Colon`. Threaded. Avoids overflow/underflow, but `+Inf` and `NaN` are not handled.
