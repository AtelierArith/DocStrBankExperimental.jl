```
ExplicitAlgorithm(tableau, [constraint])
ExplicitAlgorithm(name, [constraint])
```

Constructs an explicit algorithm for solving ODEs, with an optional name and constraint. The first constructor accepts any `ExplicitTableau` and an optional constraint, leaving the algorithm unnamed. The second constructor automatically determines the tableau and the default constraint from the algorithm name, which must be an `ERKAlgorithmName`.

Note that using an `ExplicitAlgorithm` is merely a shorthand for using an `IMEXAlgorithm` with the same tableau for explicit and implicit tendencies (and without Newton's method).
