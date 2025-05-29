```
partial_trace(X::AbstractMatrix, remove::Integer, dims::AbstractVector = _equal_sizes(X)))
```

Takes the partial trace of matrix `X` with subsystem dimensions `dims` over the subsystem `remove`. If the argument `dims` is omitted two equally-sized subsystems are assumed.
