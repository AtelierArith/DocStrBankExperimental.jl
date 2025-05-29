```
DiffEqBase.ODEProblem(sys::FSPSystem, u0, tmax[, p])
```

Return an `ODEProblem` for use in `DifferentialEquations`. This function implicitly calls `convert(ODEFunction, sys)`. It is usually more efficient to create an `ODEFunction`  first and then use that to create `ODEProblem`s.
