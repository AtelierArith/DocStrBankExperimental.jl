```
@control opera call [id]
@control agent call [id]
```

Add a control to the system. Optionally, provide a textual identifier `id` of the action.

`call` is an expression, which will be wrapped into an anonymous, parameterless function `() -> call`.

See also [`Opera`](@ref).

# Examples

```julia
system = MyAgentType("system")
control = agent -> agent.temp > 100 && cool!(agent)
@control system control(system) "temperature control"
```
