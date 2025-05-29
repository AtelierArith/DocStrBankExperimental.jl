```
transpose_vecs(input::Vararg{Vec{N,T}, L}) where {L,N,T}
```

Transposes a matrix of L vectors of size N into N vectors of size L. Sizes should be powers of 2.
