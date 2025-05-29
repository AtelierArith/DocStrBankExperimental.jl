`stan_optimize(...)`

Optimize a StanJulia OptimizationModel <: CmdStanModel

# Extended help

### Dispatch arguments

```julia
* `m:: OptimizeModel`             # CmdStanModel subtype
* `use_json=true`                 # Use JSON3 for data and init files
```

### Keyword arguments

```julia
* `init`                               : Init dict
* `data`                               : Data dict
```

```julia
stan_run(m; ...)
stan_run(m, use_json; kwargs...)

```

### Returns

```julia
* `rc`                                 # Return code, 0 is success.
```

See extended help for other keyword arguments ( `??stan_optimize` ).

# Extended help

### Additional configuration keyword arguments

```julia
* `num_chains=4`                       # Update number of chains.
* `num_threads=8`                      # Update number of threads.

* `seed=-1`                            # Set seed value.
* `init_bound=2`                       # Boundary for initialization
* `refresh=200`                        # Stream to output

* `algorithm=:lbfgs`                   # Algorithms: :lbfgs, bfgs or :newton.
* `init_alpha=0.0001`                  # Line search step size first iteration.
* `tol_obj=9.999e-13`                  # Convergence tolerance
* `tol_rel_obj=9.999e-13`              # Relative convergence tolerance
* `tol_grad=9.999e-13`                 # Convergence tolerance on norm of gradient
* `tol_rel_grad=9.999e-13`             # Relative convergence tolerance
* `tol_param=1e-8`                     # Convergence tolerance on param changes

* `history_size=`                      # Amount of history to keep for L-BFGS

* `iter=200`                           # Total number of Newton iterations
* `save_iterations=0`                  # Stream iterations to output
```
