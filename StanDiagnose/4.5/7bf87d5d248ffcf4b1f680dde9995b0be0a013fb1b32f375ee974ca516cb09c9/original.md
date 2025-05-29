stan_sample()

Draw from a StanJulia SampleModel (<: CmdStanModel.)

## Required argument

```julia
* `m <: CmdStanModels`                 # SampleModel.
* `use_json=true`                      # Use JSON3 for data and init files
* `check_num_chains=true`              # Check for correct Julia chains and C++ chains
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

* `num_samples=1000`                   # Number of samples.
* `num_warmups=1000`                   # Number of warmup samples.
* `save_warmup=false`                  # Save warmup samples.

* `thin=1`                             # Set thinning value.
* `refresh=100`                        # Output refresh rate.
* `seed=-1`                            # Set seed value.

* `test=:gradient`                     # Test :gradient.
* `epsilon=1e-8`                       # Finite difference step size.
* `error=1e-8`                         # Error threshold.
```
