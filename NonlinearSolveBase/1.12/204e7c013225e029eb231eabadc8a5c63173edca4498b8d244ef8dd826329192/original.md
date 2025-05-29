```
construct_linear_solver(alg, linsolve, A, b, u; stats, kwargs...)
```

Construct a cache for solving linear systems of the form `A * u = b`. Following cases are handled:

1. `A` is Number, then we solve it with `u = b / A`
2. `A` is `SMatrix`, then we solve it with `u = A \ b` (using the defaults from base Julia) (unless a preconditioner is specified)
3. If `linsolve` is `\`, then we solve it with directly using `ldiv!(u, A, b)`
4. In all other cases, we use `alg` to solve the linear system using [LinearSolve.jl](https://github.com/SciML/LinearSolve.jl)

### Solving the System

```julia
(cache::LinearSolverCache)(;
    A = nothing, b = nothing, linu = nothing, reuse_A_if_factorization = false, kwargs...
)
```

Returns the solution of the system `u` and stores the updated cache in `cache.lincache`.

#### Special Handling for Rank-deficient Matrix `A`

If we detect a failure in the linear solve (mostly due to using an algorithm that doesn't support rank-deficient matrices), we emit a warning and attempt to solve the problem using Pivoted QR factorization. This is quite efficient if there are only a few rank-deficient that originate in the problem. However, if these are quite frequent for the main nonlinear system, then it is recommended to use a different linear solver that supports rank-deficient matrices.

#### Keyword Arguments

  * `reuse_A_if_factorization`: If `true`, then the factorization of `A` is reused if possible. This is useful when solving the same system with different `b` values. If the algorithm is an iterative solver, then we reset the internal linear solve cache.

One distinct feature of this compared to the cache from LinearSolve is that it respects the aliasing arguments even after cache construction, i.e., if we passed in an `A` that `A` is not mutated, we do this by copying over `A` to a preconstructed cache.
