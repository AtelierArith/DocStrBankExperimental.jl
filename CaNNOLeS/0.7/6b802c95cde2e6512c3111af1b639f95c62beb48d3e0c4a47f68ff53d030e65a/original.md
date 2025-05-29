```
cannoles(nls)
```

Implementation of a solver for Nonlinear Least Squares with nonlinear constraints.

$min   f(x) = ¹/₂‖F(x)‖²   s.t.  c(x) = 0$

For advanced usage, first define a `CaNNOLeSSolver` to preallocate the memory used in the algorithm, and then call `solve!`:

```
solver = CaNNOLeSSolver(nls; linsolve = :ma57)
solve!(solver, nls; kwargs...)
```

or even pre-allocate the output:

```
stats = GenericExecutionStats(nls)
solve!(solver, nls, stats; kwargs...)
```

# Arguments

  * `nls :: AbstractNLSModel{T, V}`: nonlinear least-squares model created using `NLPModels`.

# Keyword arguments

  * `x::AbstractVector = nls.meta.x0`: the initial guess;
  * `λ::AbstractVector = nls.meta.y0`: the initial Lagrange multiplier;
  * `use_initial_multiplier::Bool = false`: if `true` use `λ` for the initial stopping tests;
  * `method::Symbol = :Newton`: available methods `:Newton, :LM, :Newton_noFHess`, and `:Newton_vanishing`;
  * `linsolve::Symbol = :ma57`: solver to compute LDLt factorization. Available methods are: `:ma57`, `:ldlfactorizations`;
  * `max_iter::Int = -1`: maximum number of iterations;
  * `max_eval::Real = 100000`: maximum number of evaluations computed by `neval_residual(nls) + neval_cons(nls)`;
  * `max_time::Float64 = 30.0`: maximum time limit in seconds;
  * `max_inner::Int = 10000`: maximum number of inner iterations (return stalled if this limit is reached);
  * `atol::T = √eps(T)`: absolute tolerance;
  * `rtol::T = √eps(T)`: relative tolerance: the algorithm uses `ϵtol := atol + rtol * ‖∇F(x⁰)ᵀF(x⁰) - ∇c(x⁰)ᵀλ⁰‖`;
  * `Fatol::T = √eps(T)`: absolute tolerance on the residual;
  * `Frtol::T = eps(T)`: relative tolerance on the residual, the algorithm stops when ‖F(xᵏ)‖ ≤ Fatol + Frtol * ‖F(x⁰)‖  and ‖c(xᵏ)‖∞ ≤ √ϵtol;
  * `verbose::Int = 0`: if > 0, display iteration details every `verbose` iteration;
  * `always_accept_extrapolation::Bool = false`: if `true`, run even if the extrapolation step fails;
  * `δdec::Real = T(0.1)`: reducing factor on the parameter `δ`.

The algorithm stops when $‖c(xᵏ)‖∞ ≤ ϵtol$ and $‖∇F(xᵏ)ᵀF(xᵏ) - ∇c(xᵏ)ᵀλᵏ‖ ≤ ϵtol * max(1, ‖λᵏ‖ / 100ncon)$.

# Output

The value returned is a `GenericExecutionStats`, see `SolverCore.jl`.

# Callback

The callback is called at each iteration. The expected signature of the callback is `callback(nls, solver, stats)`, and its output is ignored. Changing any of the input arguments will affect the subsequent iterations. In particular, setting `stats.status = :user` will stop the algorithm. All relevant information should be available in `nlp` and `solver`. Notably, you can access, and modify, the following:

  * `solver.x`: current iterate;
  * `solver.cx`: current value of the constraints at `x`;
  * `stats`: structure holding the output of the algorithm (`GenericExecutionStats`), which contains, among other things:

      * `stats.solution`: current iterate;
      * `stats.multipliers`: current Lagrange multipliers wrt to the constraints;
      * `stats.primal_feas`:the primal feasibility norm at `solution`;
      * `stats.dual_feas`: the dual feasibility norm at `solution`;
      * `stats.iter`: current iteration counter;
      * `stats.objective`: current objective function value;
      * `stats.status`: current status of the algorithm. Should be `:unknown` unless the algorithm has attained a stopping criterion. Changing this to anything will stop the algorithm, but you should use `:user` to properly indicate the intention.
      * `stats.elapsed_time`: elapsed time in seconds.

# Examples

```jldoctest
using CaNNOLeS, ADNLPModels
nls = ADNLSModel(x -> x, ones(3), 3)
stats = cannoles(nls, linsolve = :ldlfactorizations, verbose = 0)
stats

# output

"Execution stats: first-order stationary"
```

```jldoctest
using CaNNOLeS, ADNLPModels
nls = ADNLSModel(x -> x, ones(3), 3)
solver = CaNNOLeSSolver(nls, linsolve = :ldlfactorizations)
stats = solve!(solver, nls, verbose = 0)
stats

# output

"Execution stats: first-order stationary"
```
