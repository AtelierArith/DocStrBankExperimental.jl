```
trace_replace(X::AbstractMatrix, remove::AbstractVector, dims::AbstractVector = _equal_sizes(X))
```

Takes the partial trace of matrix `X` with subsystem dimensions `dims` over the subsystems in `remove` and replace them with normalized identity. If the argument `dims` is omitted two equally-sized subsystems are assumed.
