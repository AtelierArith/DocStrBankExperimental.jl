```
symmetric_setindex!(Q::VectorizedHermitianMatrix, value, i::Integer, j::Integer)
```

Set `Q[i, j]` to the value `value` and `Q[j, i]` to the value `-value`.
