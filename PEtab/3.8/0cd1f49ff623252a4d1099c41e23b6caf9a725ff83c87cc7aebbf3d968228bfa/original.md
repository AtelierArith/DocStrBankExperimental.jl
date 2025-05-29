```
PEtabMultistartResult
```

Parameter estimation statistics from multi-start optimization with `calibrate_multistart`.

See also [`calibrate_multistart`](@ref) and [`PEtabOptimisationResult`](@ref).

## Fields

  * `xmin`: Best minimizer across all runs.
  * `fmin`: Best minimum across all runs.
  * `alg`: Parameter estimation algorithm.
  * `nmultistarts`: Number of parameter estimation runs.
  * `sampling_method`: Sampling method used for generating starting points.
  * `dirsave`: Path of directory where parameter estimation run statistics are saved if   `dirsave` was provided to `calibrate_multistart`.
  * `runs`: Vector of `PEtabOptimisationResult` with the parameter estimation results   for each run.

```
PEtabMultistartResult(dirres::String; which_run::String="1")
```

Import multistart parameter estimation results saved at `dirres`.

Each time a new optimization run is performed, results are saved with unique numerical endings. Results from a specific run can be retrieved by specifying the numerical ending with `which_run`.
