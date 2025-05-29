```
current_state(ds::DynamicalSystem) → u::AbstractArray
```

Return the current state of `ds`. This state is mutated when `ds` is mutated. See also [`initial_state`](@ref), [`observe_state`](@ref).
