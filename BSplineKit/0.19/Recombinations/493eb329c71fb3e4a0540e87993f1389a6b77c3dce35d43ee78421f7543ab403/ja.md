```
nzrows(A::RecombineMatrix, col::Integer) -> UnitRange{Int}
```

`A[i, col]` がゼロでない行インデックス `i` の範囲を返します。
