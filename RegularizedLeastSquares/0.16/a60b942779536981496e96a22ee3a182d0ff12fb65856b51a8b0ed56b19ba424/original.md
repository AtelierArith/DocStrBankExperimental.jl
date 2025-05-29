```
isapplicable(solverType::Type{<:AbstractLinearSolver}, A, x, reg)
```

return `true` if a `solver` of type `solverType` is applicable to system matrix `A`, data `x` and regularization terms `reg`.
