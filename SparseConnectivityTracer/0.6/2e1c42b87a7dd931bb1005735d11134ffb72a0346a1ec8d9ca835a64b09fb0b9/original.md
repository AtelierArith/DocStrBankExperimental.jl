```
jacobian_buffer(x, detector)
```

Allocate a buffer similiar to `x` with the required tracer type for Jacobian sparsity detection. Thin wrapper around `similar` that doesn't expose internal types.
