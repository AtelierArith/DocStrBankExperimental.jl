```julia
solve(
    prob::HighDimPDE.ParabolicPDEProblem,
    pdealg::HighDimPDE.NNStopping,
    sdealg;
    verbose,
    maxiters,
    trajectories,
    dt,
    ensemblealg,
    kwargs...
) -> NamedTuple{(:payoff, :stopping_time), <:Tuple{Any, Any}}

```

Returns a NamedTuple with `payoff` and `stopping_time`

Arguments: 

  * `sdealg`: a SDE solver from [DifferentialEquations.jl](https://diffeq.sciml.ai/stable/solvers/sde_solve/).    If not provided, the plain vanilla [DeepBSDE](https://arxiv.org/abs/1707.02568) method will be applied.   If provided, the SDE associated with the PDE problem will be solved relying on    methods from DifferentialEquations.jl, using [Ensemble solves](https://diffeq.sciml.ai/stable/features/ensemble/)    via `sdealg`. Check the available `sdealg` on the    [DifferentialEquations.jl doc](https://diffeq.sciml.ai/stable/solvers/sde_solve/).
  * `maxiters`: The number of training epochs. Defaults to `300`
  * `trajectories`: The number of trajectories simulated for training. Defaults to `100`
  * Extra keyword arguments passed to `solve` will be further passed to the SDE solver.
