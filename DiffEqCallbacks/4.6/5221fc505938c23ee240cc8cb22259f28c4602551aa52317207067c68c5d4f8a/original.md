```julia
PeriodicCallback(f, Δt::Number; phase = 0, initial_affect = false,
    final_affect = false,
    kwargs...)
```

`PeriodicCallback` can be used when a function should be called periodically in terms of integration time (as opposed to wall time), i.e. at `t = tspan[1]`, `t = tspan[1] + Δt`, `t = tspan[1] + 2Δt`, and so on.

If a non-zero `phase` is provided, the invocations of the callback will be shifted by `phase` time units, i.e., the calls will occur at `t = tspan[1] + phase`, `t = tspan[1] + phase + Δt`, `t = tspan[1] + phase + 2Δt`, and so on.

This callback can, for example, be used to model a discrete-time controller for a continuous-time system, running at a fixed rate.

## Arguments

  * `f` the `affect!(integrator)` function to be called periodically
  * `Δt` is the period

## Keyword Arguments

  * `phase` is a phase offset
  * `initial_affect` is whether to apply the affect at the initial time, which defaults to `false`
  * `final_affect` is whether to apply the affect at the final time, which defaults to `false`
  * `kwargs` are keyword arguments accepted by the `DiscreteCallback` constructor.
