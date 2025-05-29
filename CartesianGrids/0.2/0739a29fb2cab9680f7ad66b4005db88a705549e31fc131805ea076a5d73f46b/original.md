```
helmholtz!(v,w,α)
```

Evaluate the discrete Helmholtz operator (iα - L) on `w` and return it as `v`. The data `w` can be of type dual/primary nodes or edges; `v` must be of the same type. However, both have to be of complex data type.
