Type for storing the vectors required by the in-place version of CG.

The outer constructors

```
solver = CgSolver(m, n, S)
solver = CgSolver(A, b)
solver = CgSolver(kc::KrylovConstructor)
```

may be used in order to create these vectors.
