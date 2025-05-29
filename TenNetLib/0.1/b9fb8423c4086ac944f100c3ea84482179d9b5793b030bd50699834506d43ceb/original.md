```
function eig_solver(env, phi0::ITensor, time_step::Nothing; kwargs...)
```

Solver to find smallest eigenvalue corresponding to "matrix" `env` and input vector `phi0`.

#### Named arguments for `solver` and their default values:

See the documentation of KrylovKit.jl.

  * `ishermitian::Bool = true`
  * `solver_tol::Float64 = 1E-14`.
  * `solver_krylovdim::Int = 5`.
  * `solver_maxiter::Int = 2`.
  * `solver_outputlevel::Int = 0`: See `verbosity` in KrylovKit.jl.
  * `solver_eager::Bool = false`.
  * `solver_check_convergence::Bool = false`.

#### Return values:

  * `::Float64`: Smallest eigenvalue.
  * `::ITensor`: Eigenstate corresponding to the smallest eigenvalue.
