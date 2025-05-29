```
MultipleShooting(; nshoots::Int, ode_alg = nothing, nlsolve = nothing,
    grid_coarsening = true, jac_alg = nothing)
MultipleShooting(nshoots::Int; kwargs...)
MultipleShooting(nshoots::Int, ode_alg; kwargs...)
MultipleShooting(nshoots::Int, ode_alg, nlsolve; kwargs...)
```

Multiple Shooting method, reduces BVP to an initial value problem and solves the IVP. Significantly more stable than Single Shooting.

## Arguments

  * `nshoots`: Number of shooting points.
  * `ode_alg`: ODE algorithm to use for solving the IVP. Any solver which conforms to the SciML `ODEProblem` interface can be used! (Defaults to `nothing` which will use poly-algorithm if `DifferentialEquations.jl` is loaded else this must be supplied)
  * `nlsolve`: Internal Nonlinear solver. Any solver which conforms to the SciML `NonlinearProblem` interface can be used.
  * `jac_alg`: Jacobian Algorithm used for the nonlinear solver. Defaults to `BVPJacobianAlgorithm()`, which automatically decides the best algorithm to use based on the input types and problem type.

      * For `TwoPointBVProblem`, only `diffmode` is used (defaults to `AutoSparse(AutoForwardDiff())` if possible else `AutoSparse(AutoFiniteDiff())`).
      * For `BVProblem`, `bc_diffmode` and `nonbc_diffmode` are used. For `nonbc_diffmode` we default to `AutoSparse(AutoForwardDiff())` if possible else `AutoSparse(AutoFiniteDiff())`. For `bc_diffmode`, we default to `AutoForwardDiff` if possible else `AutoFiniteDiff`.
  * `grid_coarsening`: Coarsening the multiple-shooting grid to generate a stable IVP solution. Possible Choices:

      * `true`: Halve the grid size, till we reach a grid size of 1.
      * `false`: Do not coarsen the grid. Solve a Multiple Shooting Problem and finally solve a Single Shooting Problem.
      * `AbstractVector{<:Int}` or `Ntuple{N, <:Integer}`: Use the provided grid coarsening. For example, if `nshoots = 10` and `grid_coarsening = [5, 2]`, then the grid will be coarsened to `[5, 2]`. Note that `1` should not be present in the grid coarsening.
      * `Function`: Takes the current number of shooting points and returns the next number of shooting points. For example, if `nshoots = 10` and `grid_coarsening = n -> n ÷ 2`, then the grid will be coarsened to `[5, 2]`.
