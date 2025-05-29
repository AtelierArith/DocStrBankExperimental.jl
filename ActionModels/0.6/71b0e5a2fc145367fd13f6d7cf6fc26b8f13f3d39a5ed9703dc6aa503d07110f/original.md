```
get_states(agent::Agent, target_state::Union{String,Tuple})
```

Get a single state from an agent. Returns a single value.

```
get_states(agent::Agent, target_state::Vector)
```

Get a set of state values from an agent. Returns a dictionary of state names and their values.

```
get_states(agent::Agent)
```

Get all states from an agent. Returns a dictionary of state names and their values.
