```
IMEXAlgorithm(tableau, newtons_method, [constraint])
IMEXAlgorithm(name, newtons_method, [constraint])
```

Constructs an IMEX algorithm for solving ODEs, with an optional name and constraint. The first constructor accepts any `IMEXTableau` and an optional constraint, leaving the algorithm unnamed. The second constructor automatically determines the tableau and the default constraint from the algorithm name, which must be an `IMEXARKAlgorithmName`.
