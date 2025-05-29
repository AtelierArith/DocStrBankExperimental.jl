```
ModifiedGramSchmidtIR(η::Real = 1/sqrt(2))
```

Represents the modified Gram Schmidt algorithm with iterative (i.e. zero or more) reorthogonalization until the norm of the vector after an orthogonalization step has not decreased by a factor smaller than `η` with respect to the norm before the step. The default value corresponds to the Daniel-Gragg-Kaufman-Stewart condition.
