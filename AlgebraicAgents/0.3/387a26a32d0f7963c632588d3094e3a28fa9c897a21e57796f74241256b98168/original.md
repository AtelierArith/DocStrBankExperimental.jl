```
@call agent call [priority[, id]]
@call opera call [priority[, id]]
```

Schedule an interaction (call), which will be executed in the current time step. Here, `call` will translate into a function `() -> call`.

Interactions are implemented within an instance `Opera`, sorted by their priorities.

See also [`Opera`](@ref).

# Examples

```julia
bob_agent = only(getagent(agent, r"bob"))
@call agent wake_up(bob_agent) # translates into `() -> wake_up(bob_agent)`
```
