```
interpolate(mesh,vector,x;fast)
```

Interpolate a vector `vector` of values on a uniform collocation grid defined by `mesh`, on collocation points given by `x`.

If the collocation points `x` are regularly spaced and the optional keyword argument `fast` is set to `true` (default is `false`), then the algorithm is faster and uses less allocations, but is less precise.

Return the vector of values on collocation points.
