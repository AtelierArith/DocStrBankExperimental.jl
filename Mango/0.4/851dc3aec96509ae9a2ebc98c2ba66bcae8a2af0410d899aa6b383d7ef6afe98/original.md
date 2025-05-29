```
add_agent_composed_of(container, roles::Role...; suggested_aid::Union{Nothing,String}=nothing, base_agent::Union{Nothing,Agent}=nothing)
```

Create an agent which is composed of the given roles `roles...` and register the agent  to the `container`. 

If no `base_agent` is provided the agent struct used is an empty struct, which is  only used as a container for the roles. The agent will be returned by the function.

# Examples

```julia
agent = add_agent_composed_of(your_container, RoleA(), RoleB(), RoleC())
```
