```
get_history(agent::Agent, target_state::Union{String,Tuple})
```

Get the history of a single state from an agent. Returns a vector.

```
get_history(agent::Agent, target_states::Vector)
```

Get set of a vector of states from an agent. Returns a dictionary of states and their histories.

```
get_history(agent::Agent)
```

Get histories for states from an agent. Returns a dictionary of states and their histories.
