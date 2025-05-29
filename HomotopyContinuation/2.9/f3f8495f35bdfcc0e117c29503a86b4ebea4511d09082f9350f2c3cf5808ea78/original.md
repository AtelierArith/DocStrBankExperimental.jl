```
TrackerOptions(; options...)
```

The set of options for a [`Tracker`](@ref).

## Options

  * `automatic_differentiation = 1`: The value `automatic_differentiation` determines up to which order the derivative is computed using automatic differentiation. Otherwise numerical differentiation is used. The automatic differentiation results in additional compilation time, however for numerically challenging paths it is strongly recommended to use `automatic_differentiation = 3`.
  * `max_steps = 10_000`: The maximal number of steps a tracker attempts
  * `max_step_size = Inf`: The maximal size of a step
  * `max_initial_step_size = Inf`: The maximal size of the first step
  * `min_step_size = 1e-48`: The minimal step size. If a smaller step size would be necessary, then the tracking gets terminated.
  * `extended_precision = true`: Whether to allow for the use of extended precision, if necessary, in some computations. This can greatly improve the ability to track numerically difficult paths.
  * `terminate_cond = 1e13`: If the relative component-wise condition number `cond(H_x, ẋ)` is larger than `terminate_cond` then the path is terminated as too ill-conditioned.
  * `parameters::Union{Symbol,TrackerParameters} = :default` Set the [`TrackerParameters`](@ref) to control the performance of the path tracking algorithm. The values `:default`, `:conservative` and `:fast` are shorthands for using [`DEFAULT_TRACKER_PARAMETERS`](@ref), [`CONSERVATIVE_TRACKER_PARAMETERS`](@ref) resp. [`FAST_TRACKER_PARAMETERS`](@ref).
