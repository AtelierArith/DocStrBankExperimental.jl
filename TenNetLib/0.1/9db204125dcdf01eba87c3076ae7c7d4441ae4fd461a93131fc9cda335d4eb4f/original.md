```
function exp_solver(env, phi0::ITensor, time_step::Union{Float64, ComplexF64}; kwargs...)
```

Exponentiation solver to find `exp(env * phi0 * time_step)`.

#### Named arguments for `solver` and their default values:

See the documentation of KrylovKit.jl.

  * `ishermitian::Bool = true`
  * `solver_tol::Float64 = 1E-12`.
  * `solver_krylovdim::Int = 30`.
  * `solver_maxiter::Int = 10`.
  * `solver_outputlevel::Int = 0`: See `verbosity` in KrylovKit.jl.
  * `solver_eager::Bool = true`.
  * `solver_check_convergence::Bool = true`.

#### Return values:

  * `::Float64`: `NaN`.
  * `::ITensor`: Exponentiated `ITensor`.
