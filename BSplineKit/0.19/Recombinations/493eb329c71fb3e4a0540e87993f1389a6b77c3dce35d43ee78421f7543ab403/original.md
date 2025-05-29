```
nzrows(A::RecombineMatrix, col::Integer) -> UnitRange{Int}
```

Returns the range of row indices `i` such that `A[i, col]` is non-zero.
