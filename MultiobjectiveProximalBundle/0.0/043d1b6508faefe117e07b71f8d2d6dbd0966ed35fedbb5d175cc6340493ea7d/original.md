```
MPBOptions(; kwargs...)
```

Options to configure the algorithm. An instance of type `MPBOptions` can be passed to optimization methods with the keyword argument `options`.

Possible `kwargs` for `MPBOptions` are:

  * `max_iter`: Maximum number of iterations (default: 1000). Default: 1000
  * `max_fun_calls`: Maximum number of function evaluations (default: 1000). Default: 1000
  * `mL`: Line-search parameter for determination of $tL ∈ [0,1]$ (default: 1e-2). Default: 0.01
  * `mR`: Line-search parameter for determination of $tR$ (default: 0.5). Default: 0.5
  * `t_bar`: Line-search parameter for classification of long or short steps (default: 1e-2). Default: 0.01
  * `t_min`: Minimum stepsize tested in line-search (default: `eps(Float64)*1e2`). Default: eps(Float64) * 100.0
  * `max_fun_calls_ls`: Maximum number of function calls in line-search (default: 100). Default: 100
  * `gamma_default`: Fallback non-convexity constant if none are provided (default: 0.5). Default: 0.5
  * `tol_acc`: Final accuracy tolerance (default: 1e-5). Default: 1.0e-5
  * `initial_weight`: Initial weight $u^1$ (default: NaN). Default: NaN
  * `max_subgrads`: Maximum number of stored subgradients (default: 10). Default: 10
