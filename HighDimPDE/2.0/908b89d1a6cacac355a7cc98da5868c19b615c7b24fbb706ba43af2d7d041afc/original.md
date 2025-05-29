```julia
solve(
    prob::HighDimPDE.ParabolicPDEProblem,
    pdealg::HighDimPDE.DeepBSDE,
    sdealg;
    verbose,
    maxiters,
    trajectories,
    dt,
    pabstol,
    save_everystep,
    limits,
    ensemblealg,
    trajectories_upper,
    trajectories_lower,
    maxiters_limits,
    kwargs...
) -> Any

```

Returns a `PIDESolution` object.

# Arguments

  * `sdealg`: a SDE solver from [DifferentialEquations.jl](https://diffeq.sciml.ai/stable/solvers/sde_solve/).    If not provided, the plain vanilla [DeepBSDE](https://arxiv.org/abs/1707.02568) method will be applied.   If provided, the SDE associated with the PDE problem will be solved relying on    methods from DifferentialEquations.jl, using [Ensemble solves](https://diffeq.sciml.ai/stable/features/ensemble/)    via `sdealg`. Check the available `sdealg` on the    [DifferentialEquations.jl doc](https://diffeq.sciml.ai/stable/solvers/sde_solve/).
  * `limits`: if `true`, upper and lower limits will be calculated, based on    [Deep Primal-Dual algorithm for BSDEs](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=3071506).
  * `maxiters`: The number of training epochs. Defaults to `300`
  * `trajectories`: The number of trajectories simulated for training. Defaults to `100`
  * Extra keyword arguments passed to `solve` will be further passed to the SDE solver.
