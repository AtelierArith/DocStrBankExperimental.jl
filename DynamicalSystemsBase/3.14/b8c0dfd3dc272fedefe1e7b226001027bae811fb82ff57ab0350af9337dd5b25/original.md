```
reinit!(ds::DynamicalSystem, u = initial_state(ds); kwargs...) → ds
```

Reset the status of `ds`, so that it is as if it has be just initialized with initial state `u`. Practically every function of the ecosystem that evolves `ds` first calls this function on it. Besides the new state `u`, you can also configure the keywords `t0 = initial_time(ds)` and `p = current_parameters(ds)`.

```
reinit!(ds::DynamicalSystem, u::AbstractDict; kwargs...) → ds
```

If `u` is a `AbstractDict` (for partially setting specific state variables in [`set_state!`](@ref)), then the alterations are done in the state given by the keyword `reference_state = copy(initial_state(ds))`.

```
reinit!(ds, ::Nothing; kwargs...)
```

This method does nothing and leaves the system as is. This is so that downstream functions that call `reinit!` can still be used without resetting the system but rather continuing from its exact current state.
