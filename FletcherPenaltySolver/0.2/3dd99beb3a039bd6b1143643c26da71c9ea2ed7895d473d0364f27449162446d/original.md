```
fps_solve(nlp::AbstractNLPModel{T, S}, x0::S = nlp.meta.x0; subsolver_verbose::Int = 0, kwargs...)
```

Compute a local minimum of a bound and equality-constrained optimization problem using Fletcher's penalty function and the implementation described in

```
Estrin, R., Friedlander, M. P., Orban, D., & Saunders, M. A. (2020).
Implementing a smooth exact penalty function for equality-constrained nonlinear optimization.
SIAM Journal on Scientific Computing, 42(3), A1809-A1835.
https://doi.org/10.1137/19M1238265
```

For advanced usage, the principal call to the solver uses a `NLPStopping`, see `Stopping.jl`.

```
fps_solve(stp::NLPStopping, fpssolver::FPSSSolver{T, QDS, US}; subsolver_verbose::Int = 0)
fps_solve(stp::NLPStopping; subsolver_verbose::Int = 0, kwargs...)
```

# Arguments

  * `nlp::AbstractNLPModel`: the model solved, see `NLPModels.jl`;
  * `x`: Initial guess. If `x` is not specified, then `nlp.meta.x0` is used.

# Keyword arguments

  * `fpssolver`: see [`FPSSSolver`](@ref);
  * `verbose::Int = 0`: if > 0, display iteration information of the solver;
  * `subsolver_verbose::Int = 0`: if > 0, display iteration information of the subsolver;

All the information regarding stopping criteria can be set in the `NLPStopping` object. Additional `kwargs` are given to the `NLPStopping`. By default, the optimality condition used to declare optimality is [`Fletcher_penalty_optimality_check`](@ref).

# Output

The returned value is a `GenericExecutionStats`, see `SolverCore.jl`.

If one define a `Stopping` before calling `fps_solve`, it is possible to access all the information computed by the algorithm.

# Notes

  * If the problem has inequalities, we use slack variables to get only equalities and bounds via `NLPModelsModifiers.jl`.
  * `stp.current_state.res` contains the gradient of Fletcher's penalty function.
  * `subproblem_solver` must take an `NLPStopping` as input, see `StoppingInterface.jl`.

# Callback

The callback is called at each iteration. The expected signature of the callback is `callback(nlp, solver, stats)`, and its output is ignored. Changing any of the input arguments will affect the subsequent iterations. In particular, setting `stats.status = :user` will stop the algorithm. All relevant information should be available in `nlp` and `solver`. Notably, you can access, and modify, the following:

  * `solver`: see [`FPSSSolver`](@ref)
  * `stats`: structure holding the output of the algorithm (`GenericExecutionStats`), which contains, among other things:

      * `stats.dual_feas`: norm of current gradient of the Lagrangian;
      * `stats.primal_feas`: norm of current feasibility;
      * `stats.iter`: current iteration counter;
      * `stats.objective`: current objective function value;
      * `stats.solution`: current iterate;
      * `stats.multipliers`: current Lagrange multipliers estimate;
      * `stats.multipliers_L` and `stats.multipliers_U`: current Lagrange multipliers estimate for the lower and upper bounds respectively;
      * `stats.status`: current status of the algorithm. Should be `:unknown` unless the algorithm has attained a stopping criterion. Changing this to anything will stop the algorithm, but you should use `:user` to properly indicate the intention.
      * `stats.elapsed_time`: elapsed time in seconds.

# Examples

```julia
julia> using FletcherPenaltySolver, ADNLPModels
julia> nlp = ADNLPModel(x -> 100 * (x[2] - x[1]^2)^2 + (x[1] - 1)^2, [-1.2; 1.0]);
julia> stats = fps_solve(nlp)
"Execution stats: first-order stationary"
```
