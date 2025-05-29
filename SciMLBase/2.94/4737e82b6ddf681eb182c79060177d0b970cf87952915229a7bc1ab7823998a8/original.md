```
reinit!(integrator::DEIntegrator,args...; kwargs...)
```

The reinit function lets you restart the integration at a new value.

# Arguments

  * `u0`: Value of `u` to start at. Default value is `integrator.sol.prob.u0`

# Keyword Arguments

  * `t0`: Starting timepoint. Default value is `integrator.sol.prob.tspan[1]`
  * `tf`: Ending timepoint. Default value is `integrator.sol.prob.tspan[2]`
  * `erase_sol=true`: Whether to start with no other values in the solution, or keep the previous solution.
  * `tstops`, `d_discontinuities`, & `saveat`: Cache where these are stored. Default is the original cache.
  * `reset_dt`: Set whether to reset the current value of `dt` using the automatic `dt` determination algorithm. Default is `(integrator.dtcache == zero(integrator.dt)) && integrator.opts.adaptive`
  * `reinit_callbacks`: Set whether to run the callback initializations again (and `initialize_save` is for that). Default is `true`.
  * `reinit_cache`: Set whether to re-run the cache initialization function (i.e. resetting FSAL, not allocating vectors) which should usually be true for correctness. Default is `true`.

Additionally, once can access [`auto_dt_reset!`](@ref) which will run the auto `dt` initialization algorithm.
