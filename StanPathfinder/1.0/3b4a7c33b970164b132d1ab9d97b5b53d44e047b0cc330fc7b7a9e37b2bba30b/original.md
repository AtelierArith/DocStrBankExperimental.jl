```julia
stan_run(m; ...)
stan_run(m, use_json; kwargs...)

```

Sample from a StanJulia PathfinderModel (<: CmdStanModel.)

## Required argument

```julia
* `m::PathfinderModel`                 # PathfinderModel.
* `use_json=true`                      # Use JSON3 for data files
```

Use `??stan_pathfinder` for a list of additional keyword arguments

### Returns

```julia
* `rc`                                 # Return code, 0 is success.
```

See extended help for other keyword arguments ( `??stan_sample` ).

# Extended help

### Additional configuration keyword arguments

```julia
* `num_chains=4` # Number of chains.

* `init=2` # Bound for initial values.
* `seed=rand(primes(1, 20000001), num_chains)` # Array of seed values.
* `refresh=100` # Stream to output.
* `sig_figs=-1` # Number of significant decimals used.
* `num_threads=1` # Number of threads.

* `init_alpha=0.001`
* `tol_obj=9.99999999e-13`
* `tol_rel_obj=1000`
* `tol_grad=1e-8`
* `tol_rel_grad=10000000`
* `tol_param=1e-4`

* `history_size=5`
* `num_psis_draws=1000`
* `num_paths=4`

* `psis_resample=true`
* `calculate_lp=true`
* `save_single_paths=false`
* `save_cmdstan_config=true`

* `max_lbfgs_iters=1000`
* `num_draws=1000`
* `num_elbo_draws=25`
```
