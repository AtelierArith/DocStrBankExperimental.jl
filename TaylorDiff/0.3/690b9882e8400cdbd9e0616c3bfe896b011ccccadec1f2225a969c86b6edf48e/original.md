```
derivative!(result, f, x, l, ::Val{P})
derivative!(result, f!, y, x, l, ::Val{P})
```

In-place derivative calculation APIs. `result` is expected to be pre-allocated and have the same shape as `y`.
