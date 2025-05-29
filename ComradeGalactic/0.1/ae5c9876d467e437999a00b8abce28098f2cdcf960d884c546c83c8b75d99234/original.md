```
`laplace(prob, opt, args...; kwargs...)`
```

Compute the Laplace or Quadratic approximation to the prob or posterior. The `args` and `kwargs` are passed the the GalacticOptim.solve function.

Note the quadratic approximation is in the space of the transformed posterior not the usual parameter space. This is better for constrained problems where we may run up against a boundary.
