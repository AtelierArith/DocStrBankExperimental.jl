```
fig = marginplot(sys::LTISystem [,w::AbstractVector];  balance=true, kwargs...)
marginplot(sys::Vector{LTISystem}, w::AbstractVector;  balance=true, kwargs...)
```

Plot all the amplitude and phase margins of the system(s) `sys`.

  * A frequency vector `w` can be optionally provided.
  * `balance`: Call [`balance_statespace`](@ref) on the system before plotting.
  * `adjust_phase_start`: If true, the phase will be adjusted so that it starts at -90*intexcess degrees, where `intexcess` is the integrator excess of the system.

`kwargs` is sent as argument to RecipesBase.plot.
