```
poke(agent, priority=0[, id])
```

Poke an agent in the current time step. Translates to a call `() -> _interact(agent)`, see [`@call`](@ref).

Interactions are implemented within an instance `Opera`, sorted by their priorities.

See also [`Opera`](@ref).

# Examples

```julia
poke(agent)
poke(agent, 1.) # with priority equal to 1
```
