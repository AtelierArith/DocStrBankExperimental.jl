```
IpoptOptions(; kwargs...)
```

Options for parameter estimation with `IpoptOptimizer`.

More details on the options can be found in the Ipopt [documentation](https://coin-or.github.io/Ipopt/).

See also [`IpoptOptimizer`](@ref), [`calibrate`](@ref), and [`calibrate_multistart`](@ref).

## Keyword Arguments

  * `print_level = 0`: Output verbosity level (valid values are 0 ≤ print_level ≤ 12)
  * `max_iter = 1000`: Maximum number of iterations
  * `tol = 1e-8`: Relative convergence tolerance
  * `acceptable_tol = 1e-6`: Acceptable relative convergence tolerance
  * `max_wall_time 1e20`: Maximum wall time optimization is allowed to run
  * `acceptable_obj_change_tol 1e20`: Acceptance stopping criterion based on objective   function change.
