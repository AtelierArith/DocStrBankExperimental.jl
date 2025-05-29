```
show_agent(sim, Type{T}, [id=0; max=5, neighborstate = []]) 
show_agent(sim, id=0; [max=5, neighborstate = []])
```

Display detailed information about the agent with ID `id`, or in the case that id is a value < 2^36, the information of the nth agent of type T. If `id` is 0 (the default value), a random agent of type T is selected.

Returns the ID of the agent (which is especially useful when a random agent is selected).

Keyword arguments:

`max` controls the maximal number of edges that are shown per network (per direction).

If a field of an agent on the source side of an edge is listed in the `neighborstate` vector, the value of this field will be also shown.
