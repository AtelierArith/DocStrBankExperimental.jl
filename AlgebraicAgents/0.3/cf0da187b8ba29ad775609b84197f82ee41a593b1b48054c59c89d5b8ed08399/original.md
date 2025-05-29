```
add_future!(opera, time, call[, id])
add_future!(agent, time, call[, id])
```

Schedule a (delayed) execution of `call` at `time`. Optionally, provide a textual identifier `id` of the action.

Here, `call` has to follow either of the following forms:     - be parameterless,     - be a function of `Opera` instance,     - be a function of the topmost agent in the hierarchy. This follows the dynamic dispatch.

See also [`Opera`](@ref).

# Examples

```julia
alice = MyAgentType("alice")
interact = agent -> wake_up!(agent)
add_future!(alice, 5.0, () -> interact(alice), "alice_schedule")
```
