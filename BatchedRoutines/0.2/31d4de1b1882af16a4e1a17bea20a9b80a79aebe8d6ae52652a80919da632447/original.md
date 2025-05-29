```
batched_scal!(s, X)
```

Overwrite `X[:, :, i]` with `a[i] * X[:, :, i]`, where `i` is the batch dimension.
