```
PEtabOptimisationResult
```

Parameter estimation statistics from single-start optimization with `calibrate`.

See also: [`calibrate`](@ref)

## Fields

  * `xmin`: Minimizing parameter vector found by the optimization.
  * `fmin`: Minimum objective value found by the optimization.
  * `x0`: Starting parameter vector.
  * `alg`: Parameter estimation algorithm used.
  * `niterations`: Number of iterations for the optimization.
  * `runtime`: Runtime in seconds for the optimization.
  * `xtrace`: Parameter vector optimization trace. Empty if `save_trace = false` was   provided to `calibrate`.
  * `ftrace`: Objective function optimization trace. Empty if `save_trace = false` was   provided to `calibrate`.
  * `converged`: Convergence flag from `alg`.
  * `original`: Original result struct returned by `alg`. For example, if `alg = IPNewton()`   from Optim.jl, `original` is the Optim return struct.
