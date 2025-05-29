```
add_instantious!(opera, call, priority=0[, id])
add_instantious!(agent, call, priority=0[, id])
```

Schedule a `call` to be executed in the current time step.

Interactions are implemented within an instance `Opera`, sorted by their priorities.

See also [`Opera`](@ref).

# Examples

```julia
add_instantious!(agent, () -> wake_up(agent))
```
