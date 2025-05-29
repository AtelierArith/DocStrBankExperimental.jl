Type for storing the vectors required by the in-place version of BICGSTAB.

The outer constructors

```
solver = BicgstabSolver(m, n, S)
solver = BicgstabSolver(A, b)
solver = BicgstabSolver(kc::KrylovConstructor)
```

may be used in order to create these vectors.
