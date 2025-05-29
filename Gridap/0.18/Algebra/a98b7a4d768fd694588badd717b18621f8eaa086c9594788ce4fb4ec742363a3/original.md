```
solve!(x::AbstractVector,nls::NonlinearSolver,op::NonlinearOperator)
```

Usage:

cache = solve!(x,nls,op)

The returned `cache` object can be used in subsequent solves:

cache = solve!(x,nls,op,cache)
