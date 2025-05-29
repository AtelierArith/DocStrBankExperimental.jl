```
FPSSSolver(nlp::AbstractNLPModel [, x0 = nlp.meta.x0]; kwargs...)
FPSSSolver(stp::NLPStopping; kwargs...)
```

Structure regrouping all the structure used during the `fps_solve` call. It returns a `FPSSSolver` structure.

# Arguments

The keyword arguments may include:

  * `stp::NLPStopping`: `Stopping` structure for this algorithm workflow;
  * `meta::AlgoData{T}`: see [`AlgoData`](@ref);
  * `workspace`: allocated space for the solver itself;
  * `qdsolver`: solver structure for the linear algebra part, contains allocation for this part. By default a `LDLtSolver`, but an alternative is `IterativeSolver` ;
  * `subproblem_solver::AbstractOptimizationSolver`: by default a `subproblem_solver_correspondence[Symbol(meta.subproblem_solver)]`;
  * `sub_stats::GenericExecutionStats`: stats structure for the result of `subproblem_solver`;
  * `feasibility_solver`: by default a `GNSolver`, see [`GNSolver`](@ref);
  * `model::FletcherPenaltyNLP`: subproblem;
  * `sub_stp::NLPStopping`: `Stopping` structure for the subproblem.

Note:

  * `subproblem_solver` is accessible from the `subproblem_solver_correspondence::Dict`.
  * the `qdsolver` is accessible from the dictionary `qdsolver_correspondence`.
