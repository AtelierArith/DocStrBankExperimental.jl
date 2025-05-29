```
load(hierarchy; eval_scope=Main)
```

Instantiate an agent hierarchy from a dictionary.

By default, each agent is represented as a dictionary with fields

  * `type`: type of the agent, this can be a string containing the type name or the actual type,
  * `name`: name of the agent,
  * `arguments` (unless empty): a vector of agent's properties, excluding common interface properties (such as `name`, `uuid`, `parent`, `opera`, etc.)
  * `inners` (unless empty): a vector with inner agents' representations.

For example,

```julia
Dict(
    "type" => FreeAgent, "name" => "system", 
    "inners" => [
        Dict("name" => "alice", "type" => MyAgent{Float64}, "arguments" => Any[0.0, 1.0]),
        Dict("name" => "bob", "type" => MyAgent{Float64}, "arguments" => Any[0.0, 1.5]),
    ]
)
```

Internally, the method retrieves the type of the encapsulating agent from the provided `hierarchy` dictionary and then calls `_load(type, hierarchy; eval_scope)` on it. This process instantiates the encapsulating agent as well as all the associated inner agents contained within the `hierarchy`.

See also [`load`](@ref).
