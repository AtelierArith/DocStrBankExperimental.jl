```
ScalarObjective
```

Type for objective functions that return a scalar value. The type stores the objective function `f` and, if applicable, functions that compute its gradient `g`, Hessian `h`, combinations thereof (`fg`, `fgh`), and a "batched" version of the objective `batched_f` that applies `f` to all elements of an array. It may also store an addition parameter `param` passed to these functions.
