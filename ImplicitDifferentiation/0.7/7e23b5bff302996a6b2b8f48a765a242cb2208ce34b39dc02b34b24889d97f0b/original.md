```
KrylovLinearSolver
```

Callable object that can solve linear systems `Ax = b` and `AX = B` in the same way as the built-in `\`. Uses an iterative solver from [Krylov.jl](https://github.com/JuliaSmoothOptimizers/Krylov.jl) under the hood.

# Constructor

```
KrylovLinearSolver(; verbose=true)
```

If `verbose` is `true`, the solver logs a warning in case of failure. Otherwise it will fail silently, and may return solutions that do not exactly satisfy the linear system.

# Callable behavior

```
(::KylovLinearSolver)(A, b::AbstractVector)
```

Solve a linear system with a single right-hand side.

```
(::KrylovLinearSolver)(A, B::AbstractMatrix)
```

Solve a linear system with multiple right-hand sides.
