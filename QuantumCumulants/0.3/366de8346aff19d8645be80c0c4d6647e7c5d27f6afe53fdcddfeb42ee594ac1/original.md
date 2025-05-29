```
get_solution(sol, op::QTerm)
get_solution(sol, op::QNumber)
```

Returns the result for the average of the operator expression `op` in the solution `sol` of an ODE- or SteadyStateProblem, similar to `sol[op]`. It can also be used for linear combinations of operators, which is not possible with `sol[op]`.
