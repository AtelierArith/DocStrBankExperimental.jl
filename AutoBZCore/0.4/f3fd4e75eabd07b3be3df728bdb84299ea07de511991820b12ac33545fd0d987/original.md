```
CommonSolveIntegralFunction(prob, alg, update!, postsolve, [prototype, specialize]; kws...)
```

Constructor for an integrand that solves a problem defined with the CommonSolve.jl interface, `prob`, which is instantiated using `init(prob, alg; kws...)`. Helper functions include: `update!(cache, x, p)` is called before `solve!(cache)`, followed by `postsolve(sol, x, p)`, which should return the value of the solution. The `prototype` argument can help control how much to `specialize` on the type of the problem, which defaults to `FullSpecialize()` so that run times are improved. However `FunctionWrapperSpecialize()` may help reduce compile times.
