```
step!(model::ABM)
```

Perform one simulation step for the `model`. For continuous time models, this means to run to the model up to the next event and perform that.

```
step!(model::ABM, t::Real)
```

Step the model forwards until there is a temporal difference `≥ t` from the current model time. I.e., step the model forwards for at least `t` time. For discrete time models like [`StandardABM`](@ref) `t` must be integer and evolves the model for *exactly* `t` steps.

```
step!(model::ABM, f::Function)
```

Step the model forwards until `f(model, t)` returns `true`, where `t` is the current amount of time the model has been evolved for, starting from the model's initial time.

See also [Advanced stepping](@ref advanced_stepping).
