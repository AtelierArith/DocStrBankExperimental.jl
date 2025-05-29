```
struct Edge{T} 
    from::AgentID
    state::T
end
```

An edge between to agents with (optionally) additional state. T can be also a struct without any field.

The AgentID of the agent at the target of the edge is not a field of `Edge` itself, since this information is already part of the containers in which the edges are stored.

See also [`register_edgetype!`](@ref)
