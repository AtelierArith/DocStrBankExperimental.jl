```
symmetric_setindex!(Q::VectorizedHermitianMatrix, value, i::Integer, j::Integer)
```

`Q[i, j]` を値 `value` に設定し、`Q[j, i]` を値 `-value` に設定します。
