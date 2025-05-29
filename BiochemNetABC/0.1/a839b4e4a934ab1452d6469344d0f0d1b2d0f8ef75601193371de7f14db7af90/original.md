```
abc_smc(pm::ParametricModel, l_obs, func_dist; nbr_particles, alpha, kernel_type, NT
        duration_time, bound_sim, sym_var_aut, verbose)
```

Run the ABC-SMC algorithm with the pm parametric model. 

`func_dist(l_sim, l_obs)` is the distance function between simulations and observation,  it corresponds to $\rho(\eta(y_sim), \eta(y_exp))\$. `l_obs::Vector{<:T2}` is a collection of observations. `dist` must have a signature of the form `func_dist(l_sim::Vector{T1}, l_obs::Vector{T2})`.

If `pm` is defined on a `ContinuousTimeModel`, then `T1` should verify `T1 <: Trajectory`.

!!! Distance function and distributed ABC     If you use `abc_smc` with multiple workers, `dist` has to be defined      on every workers by using @everywhere.
