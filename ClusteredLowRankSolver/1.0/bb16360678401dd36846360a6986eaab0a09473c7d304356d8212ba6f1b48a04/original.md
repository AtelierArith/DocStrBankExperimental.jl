```
Objective(constant, matrixcoeff::Dict, freecoeff::Dict)
```

The objective for the Problem.

Arguments:

  * `constant`: A constant offset of the objective value.
  * `matrixcoeff`: A `Dict` with positive semidefinite matrix variable names as keys and the objective matrices as values.
  * `freecoeff`: A `Dict` with free variable names as keys and the coefficients as values.
