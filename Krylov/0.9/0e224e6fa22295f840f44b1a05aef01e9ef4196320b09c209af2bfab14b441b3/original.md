Type for storing the vectors required by the in-place version of GMRES.

The outer constructors

```
solver = GmresSolver(m, n, memory, S)
solver = GmresSolver(A, b, memory = 20)
solver = GmresSolver(kc::KrylovConstructor, memory = 20)
```

may be used in order to create these vectors. `memory` is set to `n` if the value given is larger than `n`. `memory` is an optional argument in the second constructor.
