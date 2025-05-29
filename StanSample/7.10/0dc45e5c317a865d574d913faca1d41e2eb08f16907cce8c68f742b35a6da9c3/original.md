stan_sample()

Draw from a StanJulia SampleModel (<: CmdStanModel.)

## Required argument

```julia
* `m <: CmdStanModels`                 # SampleModel
```

### Most frequently used keyword arguments

```julia
* `data`                               # Observations Dict or NamedTuple.
* `init`                               # Init Dict or NT (default: -2 to +2).
```

See extended help for other keyword arguments ( `??stan_sample` ).

### Returns

```julia
* `rc`                                 # Return code, 0 is success.
```

# Extended help

### Additional configuration keyword arguments

```julia
* `num_threads=4`                      # Update number of c++ threads.
* `check_num_chains=true`              # Check for C++ chains or Julia level chains
* `num_cpp_chains=1`                   # Update number of c++ chains.
* `num_julia_chains=1`                 # Update number of Julia chains.
                                       # Both initialized from num_chains

* `use_cpp_chains=false`               # Run num_chains on c++ level
                                       # Set to false to use Julia processes

* `num_chains=4`                       # Actual number of chains.
* `num_samples=1000`                   # Number of samples.
* `num_warmups=1000`                   # Number of warmup samples.
* `save_warmup=false`                  # Save warmup samples.

* `thin=1`                             # Set thinning value.
* `seed=-1`                            # Set seed value.

* `engaged=true`                       # Adaptation engaged.
* `gamma=0.05`                         # Adaptation regularization scale.
* `delta=0.8`                          # Adaptation target acceptance statistic.
* `kappa=0.75`                         # Adaptation relaxation exponent.
* `t0=10`                              # Adaptation iteration offset.
* `init_buffer=75`                     # Inital adaptation interval.
* `term_buffer=50`                     # Final fast adaptation interval.
* `window=25`                          # Initia; slow adaptation interval.

* `algorithm=:hmc`                     # Sampling algorithm.
* `engine=:nuts`                       # :nuts or :static.
* `max_depth=10`                       # Max tree depth for :nuts engine.
* `int_time=2 * pi`                    # Integration time for :static engine.

* `metric=:diag_e`                     # Geometry of manifold setting:
                                       # :diag_e, :unit_e or :dense_e.
* `metric_file=""`                     # Precompiled Euclidean metric.
* `stepsize=1.0`                       # Step size for discrete evolution
* `stepsize_jitter=0.0`                # Random jitter on step size ( [%] )

* `use_json=true`                      # Set to false for .R data files.

* `sig_figs=6`                         # Number of significant digits in output files

* `summary=true`                       # Create stansummary .csv file
* `print_summary=false`                # Display summary

* `show_logging=false`                 # Display log file refreshes in terminal
```

Note: Currently I do not suggest to use both C++ level chains and Julia level chains. By default, based on  `use_cpp_chains` the `stan_sample()`  method will set either `num_cpp_chains=num_chains; num_julia_chains=1`  (the default) or `num_julia_chains=num_chains;num_cpp_chain=1`. Set the  `check_num_chains` keyword argument in the call to `stan_sample()` to  `false` to prevent this default behavior.

Threads on C++ level can be used in multiple ways, e.g. to run separate  chains and to speed up certain operations. By default StanSample.jl's  SampleModel sets the C++ num_threads to 4. See the `graphs` subdirectory in the RedCardsStudy in the Examples directory for an example.

Typically, a user should consider to generate outputs with sig_figs=18 so that the f64's are uniquely identified. It will increase .csv sizes (and might affect subsequent read times).
