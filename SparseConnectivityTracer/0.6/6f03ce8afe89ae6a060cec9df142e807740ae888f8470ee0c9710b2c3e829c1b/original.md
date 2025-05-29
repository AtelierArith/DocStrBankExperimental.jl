```
hessian_buffer(x, detector)
```

Allocate a buffer similiar to `x` with the required tracer type for Hessian sparsity detection. Thin wrapper around `similar` that doesn't expose internal types.
