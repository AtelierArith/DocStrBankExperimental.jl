```
VOMPSOptions
```

Configuration struct for VOMPS algorithm.

# Fields

  * `tol::Float64`: Convergence tolerance for VOMPS updates
  * `maxiter::Int`: Maximum number of iterations
  * `verbosity::Int`: Output verbosity level (0 = silent, 1 = basic, 2 = detailed)
  * `do_gauge_fixing::Bool`: Enable/disable gauge fixing after convergence
