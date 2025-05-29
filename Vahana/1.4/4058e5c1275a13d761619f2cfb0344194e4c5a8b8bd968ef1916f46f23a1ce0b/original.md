```
checked(f, g, itr; kwargs...)
```

Calls g(f, itr; kwargs...), but only if itr != nothing.

As all the Vahana functions that access the edges of a specific agent can return nothing in the case, that there exist no incoming edge for this agent, it's often necessery to check this case. 

Example:

Instead of writing 

```@example
nids = neighborids(sim, id, Contact)
if nids != nothing
    foreach(nids) do nid
      add_edge!(sim, id, nid, Inform()
    end
end
```

you can use the checked function to write

```@example
checked(foreach, neighborids(sim, id, Contact)) do nid
    add_edge!(sim, id, nid, Inform())
end
```
