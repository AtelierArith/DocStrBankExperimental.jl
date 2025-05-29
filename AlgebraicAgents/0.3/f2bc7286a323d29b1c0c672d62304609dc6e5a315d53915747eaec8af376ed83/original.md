```
add_control!(opera, call[, id])
add_control!(agent, call[, id])
```

Add a control to the system. Optionally, provide a textual identifier `id` of the action.

Here, `call` has to follow either of the following forms:     - be parameterless,     - be a function of `Opera` instance,     - be a function of the topmost agent in the hierarchy. This follows the dynamic dispatch.

See also [`@control`](@ref) and [`Opera`](@ref).

# Examples

```julia
system = MyAgentType("system")
control = agent -> agent.temp > 100 && cool!(agent)
add_control!(system, () -> control(system), "temperature control")
```
