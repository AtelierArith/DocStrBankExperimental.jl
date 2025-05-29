```
solve!(x::AbstractVector,nls::NonlinearSolver,op::NonlinearOperator)
```

使用法:

cache = solve!(x,nls,op)

返される`cache`オブジェクトは、後続の解決に使用できます:

cache = solve!(x,nls,op,cache)
