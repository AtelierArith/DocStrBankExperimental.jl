```
percival(nlp)
```

A factorization-free augmented Lagrangian for nonlinear optimization.

For advanced usage, first define a `PercivalSolver` to preallocate the memory used in the algorithm, and then call `solve!`:

```
solver = PercivalSolver(nlp)
solve!(solver, nlp)

stats = GenericExecutionStats(nlp)
solver = PercivalSolver(nlp)
solve!(solver, nlp, stats)
```

# Arguments

  * `nlp::AbstractNLPModel{T, V}` is the model to solve, see `NLPModels.jl`.

# Keyword arguments

  * `x::V = nlp.meta.x0`: the initial guess;
  * `atol::T = T(1e-8)`: absolute tolerance;
  * `rtol::T = T(1e-8)`: relative tolerance;
  * `ctol::T = atol > 0 ? atol : rtol`: absolute tolerance on the feasibility;
  * `max_eval::Int = 100000`: maximum number of evaluation of the objective function;
  * `max_time::Float64 = 30.0`: maximum time limit in seconds;
  * `max_iter::Int = 2000`: maximum number of iterations;
  * `verbose::Int = 0`: if > 0, display iteration details every `verbose` iteration;
  * `μ::Real = T(10.0)`: Starting value of the penalty parameter;
  * `η₀::T = T(0.5)`: Starting value for the contraints tolerance of the subproblem;
  * `ω₀::T = T(1)`: Starting value for relative tolerance of the subproblem;
  * `ω_min::T = sqrt(eps(T))`: Smallest value for relative tolerance of the subproblem;
  * `α₁::T = T(9 // 10)`: $η = max(η / al_nlp.μ^α₁, ϵp)$ if $‖c(xᵏ)‖ ≤ η$;
  * `β₀::T = T(1)`: see `β₁`;
  * `β₁::T = T(1 // 10)`: $η = max(β₀ / al_nlp.μ^β₁, ϵp)$ if $‖c(xᵏ)‖ > η$;
  * `μ_up::T = T(10)`: Multiplicative factor of `μ` if not $‖c(xᵏ)‖ > η$;
  * `subsolver_logger::AbstractLogger = NullLogger()`: logger passed to `tron`;
  * `subsolver_max_iter = typemax(Int)`: maximum number of iterations for the subsolver;
  * `subsolver_max_cgiter = nlp.meta.nvar`: subproblem's iteration limit for the subsolver;
  * `cgls_verbose::Int = 0`: verbosity level in `Krylov.cgls`;
  * `inity::Bool = false`: If `true` the algorithm uses `Krylov.cgls` to compute an approximation, otherwise we use `nlp.meta.y0`;

other `kwargs` are passed to the subproblem solver.

The algorithm stops when $‖c(xᵏ)‖ ≤ ctol$ and $‖P∇L(xᵏ,λᵏ)‖ ≤ atol + rtol * ‖P∇L(x⁰,λ⁰)‖$ where $P∇L(x,λ) := Proj_{l,u}(x - ∇f(x) + ∇c(x)ᵀλ) - x$.

# Output

The value returned is a `GenericExecutionStats`, see `SolverCore.jl`.

# Callback

The callback is called at each iteration. The expected signature of the callback is `callback(nlp, solver, stats)`, and its output is ignored. Changing any of the input arguments will affect the subsequent iterations. In particular, setting `stats.status = :user` will stop the algorithm. All relevant information should be available in `nlp` and `solver`. Notably, you can access, and modify, the following:

  * `solver.x`: current iterate;
  * `solver.gx`: current gradient;
  * `stats`: structure holding the output of the algorithm (`GenericExecutionStats`), which contains, among other things:

      * `stats.dual_feas`: norm of current projected gradient of Lagrangian;
      * `stats.primal_feas`: norm of the feasibility residual;
      * `stats.iter`: current iteration counter;
      * `stats.objective`: current objective function value;
      * `stats.multipliers`: current estimate of Lagrange multiplier associated with the equality constraint;
      * `stats.status`: current status of the algorithm. Should be `:unknown` unless the algorithm has attained a stopping criterion. Changing this to anything will stop the algorithm, but you should use `:user` to properly indicate the intention.
      * `stats.elapsed_time`: elapsed time in seconds.

# Examples

```jldoctest
using Percival, ADNLPModels
nlp = ADNLPModel(x -> sum(x.^2), ones(3), x -> [x[1]], zeros(1), zeros(1))
stats = percival(nlp)

# output

"Execution stats: first-order stationary"
```

```jldoctest
using Percival, ADNLPModels, SolverCore
nlp = ADNLPModel(x -> sum(x.^2), ones(3), x -> [x[1]], zeros(1), zeros(1))
stats = GenericExecutionStats(nlp)
solver = PercivalSolver(nlp)
stats = solve!(solver, nlp, stats)

# output

"Execution stats: first-order stationary"
```
