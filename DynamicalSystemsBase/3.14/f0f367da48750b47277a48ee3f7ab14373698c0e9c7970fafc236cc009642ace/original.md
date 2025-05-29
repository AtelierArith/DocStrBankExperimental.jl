```
trajectory(ds::DynamicalSystem, T [, u0]; kwargs...) → X, t
```

Evolve `ds` for a total time of `T` and return its trajectory `X`, sampled at equal time intervals, and corresponding time vector. `X` is a `StateSpaceSet`. Optionally provide a starting state `u0` which is `current_state(ds)` by default.

The returned time vector is `t = (t0+Ttr):Δt:(t0+Ttr+T)`.

If time evolution diverged, or in general failed, before `T`, the remaining of the trajectory is set to the last valid point.

`trajectory` is a very simple function provided for convenience. For continuous time systems, it doesn't play well with callbacks, use `DifferentialEquations.solve` if you want a trajectory/timeseries that works with callbacks, or in general you want more flexibility in the generated trajectory (but remember to convert the output of `solve` to a `StateSpaceSet`).

## Keyword arguments

  * `Δt`:  Time step of value output. For discrete time systems it must be an integer. Defaults to `0.1` for continuous and `1` for discrete time systems. If you don't have access to unicode, the keyword `Dt` can be used instead.
  * `Ttr = 0`: Transient time to evolve the initial state before starting saving states.
  * `t0 = initial_time(ds)`: Starting time.
  * `container = SVector`: Type of vector that will represent the state space points that will be included in the `StateSpaceSet` output. See `StateSpaceSet` for valid options.
  * `save_idxs::AbstractVector`: Which variables to output in `X`. It can be any type of index that can be given to [`observe_state`](@ref). Defaults to `1:dimension(ds)` (all dynamic variables). Note: if you mix integer and symbolic indexing be sure to initialize the array as `Any` so that integers `1, 2, ...` are not converted to symbolic expressions.
