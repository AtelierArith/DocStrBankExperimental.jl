stan_variational()

Sample from a StanJulia VariationalModel (<: CmdStanModel.)

## Required argument

```julia
* `m::VariationalModel`                # VariationalModel.
* `use_json=true`                      # Use JSON3 for data and init files
```

### Most frequently used keyword arguments

```julia
* `data`                               # Observations Dict or NamedTuple.
* `init`                               # Init Dict or NT (default: -2 to +2).
```

### Returns

```julia
* `rc`                                 # Return code, 0 is success.
```

See extended help for other keyword arguments ( `??stan_sample` ).

# Extended help

### Additional configuration keyword arguments

```julia
* `num_chains=4`                       # Update number of chains.
* `num_threads=8`                      # Update number of threads.

* `seed=-1`                            # Set seed value.
* `refresh=100`                        # Strem to output.
* `init_bound=2`                       # Bound for initial values.

* `algorithm=:meanfield`               # :menafield or :fullrank
* `iter=10000`                         # Maximim no of ADVI iterations
* `grad_samples=1`                     # Number of draws to compute gradient
* `elbo_samples=100`                   # Number of draws for ELBO estimate
* `eta=1.0`                            # Stepsize scaling parameter

* `engaged=true`                       # Eta adaptation active
* `adapt_iter=50`                      # No of iterations for eta adaptation

* `tol_rel_obj=0.01`                   # Tolerance for convergence
* `eval_elbo=100`                      # No of iterations between ELBO evaluations
* `output_samples=1000`                # Approximate no of posterior draws to save
```
