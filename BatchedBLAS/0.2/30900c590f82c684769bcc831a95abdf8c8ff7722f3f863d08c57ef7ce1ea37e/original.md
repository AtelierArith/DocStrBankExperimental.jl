```
batched_dot!(o, x, y)
```

In-place batched vector-vector multiplication, equivalent to `o[k] = transpose(x[:,k]) * y[:,k]` for all `k`.  All inputs can have eltypes of either AbstractFloats or Integers.
