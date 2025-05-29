```
agent_composed_of(roles::Role...; base_agent::Union{Nothing,Agent}=nothing)
```

Create an agent which is composed of the given roles `roles...`.

If no `base_agent` is provided the agent struct used is an empty struct, which is  only used as a container for the roles. The agent will be returned by the function.

# Examples

```julia
agent = agent_composed_of(RoleA(), RoleB(), RoleC())
```
