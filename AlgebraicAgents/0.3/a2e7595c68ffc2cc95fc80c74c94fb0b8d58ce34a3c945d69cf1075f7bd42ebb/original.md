```
save(agent)
```

Save an agent hierarchy into a dictionary.

By default, each agent is represented as a dictionary with fields

  * `type`: type of the agent,
  * `name`: name of the agent,
  * `arguments` (unless empty): a vector of agent's properties, excluding common interface properties (such as `name`, `uuid`, `parent`, `opera`, etc.)
  * `inners` (unless empty): a vector with inner agents' representations.

See also [`load`](@ref).

# Example

```julia
dump = save(agent)

# output
Dict(
    "type" => FreeAgent, "name" => "system", 
    "inners" => [
        Dict("name" => "alice", "type" => MyAgent{Float64}, "arguments" => Any[0.0, 1.0]),
        Dict("name" => "bob", "type" => MyAgent{Float64}, "arguments" => Any[0.0, 1.5]),
    ]
)
```
