```
@future opera time call [id]
@future agent time call [id]
```

Schedule a (delayed) execution of `call` at `time`. Optionally, provide a textual identifier `id` of the action.

`call` is an expression, which will be wrapped into a function `() -> call` (taking closure at the time when `@future` is invoked).

See also [`@future`](@ref) and [`Opera`](@ref).

# Examples

```julia
alice = MyAgentType("alice")
interact = agent -> wake_up!(agent)
@future alice 5.0 interact(alice) "alice_schedule" # stop at `t=5`
```
