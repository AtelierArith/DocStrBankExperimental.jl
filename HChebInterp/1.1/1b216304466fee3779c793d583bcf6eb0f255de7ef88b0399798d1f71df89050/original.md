```
BatchFunction(f, [x])
```

Wrapper for an out-of-place function of the form `f.(x)`, where the input `x` will be a vector with a similar element type to the input domain. Optionally provide a resizeable vector `x` to store the input points.
