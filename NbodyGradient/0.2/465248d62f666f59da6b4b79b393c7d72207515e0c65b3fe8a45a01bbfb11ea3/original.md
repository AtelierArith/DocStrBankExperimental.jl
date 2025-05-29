```
(::Integrator)(s, N; grad=true)
```

Callable [`Integrator`](@ref) method. Integrate for N steps.

# Arguments

  * `s::State{T}` : The current state of the simulation.
  * `N::Int64` : Number of steps.

### Optional

  * `grad::Bool` : Choose whether to calculate gradients. (Default = true)
