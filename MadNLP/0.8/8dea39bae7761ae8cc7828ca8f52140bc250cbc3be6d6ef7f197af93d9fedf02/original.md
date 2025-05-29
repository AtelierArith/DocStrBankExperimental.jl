```
solve!(::AbstractLinearSolver, x::AbstractVector)
```

Solve the linear system $Ax = b$.

This function assumes the linear system has been factorized previously with [`factorize!`](@ref).
