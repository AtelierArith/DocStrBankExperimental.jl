```
multi_start(nlp::AbstractNLPModel; kwargs...)
```

This function runs a simple optimization strategy that run local optimizers  for several initial guesses.

# Arguments

  * `nlp::AbstractNLPModel{T, V}` represents the model to solve, see `NLPModels.jl`.

The keyword arguments may include

  * `multi_solvers::Bool = false`: If true it runs all the available solvers, one solver otherwise;
  * `skip_solvers::Vector{String} = String[]`: If `multi_solvers` is true, the solvers in this list are skipped;
  * `N::Integer = get_nvar(nlp)`: number of additional initial guesses considered;
  * `max_time::Float64 = 60.0`: maximum time limit in seconds;
  * `verbose::Integer = 0`: if > 0, display iteration details every `verbose` iteration.
  * `solver_verbose::Integer = 0`: verbosity of the solver;
  * `strategy::Symbol = :random`: strategy to compute a next initial guess in [:random].

Other keyword arguments are passed to the solvers.
