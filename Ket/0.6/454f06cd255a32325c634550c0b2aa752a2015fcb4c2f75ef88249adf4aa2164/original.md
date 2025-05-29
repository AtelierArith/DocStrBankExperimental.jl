```
partial_transpose(X::AbstractMatrix, transp::Integer, dims::AbstractVector = _equal_sizes(X))
```

Takes the partial transpose of matrix `X` with subsystem dimensions `dims` over the subsystem `transp`. If the argument `dims` is omitted two equally-sized subsystems are assumed.
