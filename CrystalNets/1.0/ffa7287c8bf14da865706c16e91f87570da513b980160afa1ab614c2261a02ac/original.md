```
determine_topology(path, options::Options)
determine_topology(path; kwargs...)
```

Compute the topology of the structure described in the file located at `path`. This is exactly equivalent to calling `topological_genome(UnderlyingNets(parse_chemfile(path, options)))`.

Return an [`InterpenetratedTopologyResult`](@ref).
