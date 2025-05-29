```julia
solve(
    prob::HighDimPDE.ParabolicPDEProblem,
    alg::HighDimPDE.DeepBSDE;
    dt,
    abstol,
    verbose,
    maxiters,
    save_everystep,
    trajectories,
    ensemblealg,
    limits,
    trajectories_upper,
    trajectories_lower,
    maxiters_limits
)

```

Returns a `PIDESolution` object. 

# Arguments:

  * `maxiters`: The number of training epochs. Defaults to `300`
  * `trajectories`: The number of trajectories simulated for training. Defaults to `100`

To use [SDE Algorithms](https://diffeq.sciml.ai/stable/solvers/sde_solve/) use [`DeepBSDE`](@ref)
