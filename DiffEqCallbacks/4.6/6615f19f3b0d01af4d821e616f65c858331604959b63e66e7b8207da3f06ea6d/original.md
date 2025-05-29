```julia
IterativeCallback(time_choice, user_affect!, tType = Float64;
    initial_affect = false, kwargs...)
```

A callback to be used to iteratively apply some affect. For example, if given the first effect at `t₁`, you can define `t₂` to apply the next effect.

## Arguments

  * `time_choice(integrator)` determines the time of the next callback. If `nothing` is returned for the time choice, then the iterator ends.
  * `user_affect!` is the effect applied to the integrator at the stopping points.

## Keyword Arguments

  * `initial_affect` is whether to apply the affect at `t=0` which defaults to `false`
