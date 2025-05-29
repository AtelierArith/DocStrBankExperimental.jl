```
NLSolver(ls::LinearSolver;kwargs...)
NLSolver(;kwargs...)
```

Same kwargs as in `nlsolve`. If `ls` is provided, it is not possible to use the `linsolve` kw-argument.
