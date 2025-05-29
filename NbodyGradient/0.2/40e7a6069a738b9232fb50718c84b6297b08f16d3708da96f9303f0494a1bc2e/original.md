```
(::Integrator)(s; grad=true)
```

Callable [`Integrator`](@ref) method. Integrate from `s.t` to `tmax` – specified in constructor.

# Arguments

  * `s::State{T}` : The current state of the simulation.

### Optional

  * `grad::Bool` : Choose whether to calculate gradients. (Default = true)
