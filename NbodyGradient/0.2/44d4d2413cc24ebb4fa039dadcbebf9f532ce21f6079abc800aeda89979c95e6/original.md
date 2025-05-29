```
(::Integrator)(s, time; grad=true)
```

Callable [`Integrator`](@ref) method. Integrate to specific time.

# Arguments

  * `s::State{T}` : The current state of the simulation.
  * `time::T` : Time to integrate to.

### Optional

  * `grad::Bool` : Choose whether to calculate gradients. (Default = true)
