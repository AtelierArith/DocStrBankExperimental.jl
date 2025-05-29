```
shape(A[, i])
```

Return the shape of the range and domain of `A::Union{Jet, Jop, AbstractMatrix}`. With no arguments, return `(size(range(A)), size(domain(A)))`.  With `i` specified, return `size(range(A))` for `i = 1` and return `size(domain(A))` otherwise.
