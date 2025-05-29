```
spdiag(n::Int64)
```

Constructs a sparse identity matrix of size $n\times n$, which is equivalent to `spdiag(n, 0=>ones(n))`
