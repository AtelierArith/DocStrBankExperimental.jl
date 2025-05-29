```
dimnames(A) -> Tuple
dimnames(A, d) -> Symbol
```

Return the names of all the dimensions of the array `A`, or just the one for the `d`-th dimension.

Gives wildcards `:_` if this is not a `NamedDimsArray`. Like `size(A, d)`, it allows `d > ndims(A)`, in this case all the trailing dimension are given the wildcard name (`:_`).
