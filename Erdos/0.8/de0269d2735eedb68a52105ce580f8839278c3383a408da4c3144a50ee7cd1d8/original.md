```
mutable struct PropertyStore
    gmaps::Dict{String, Any}
    emaps::Dict{String,AEdgeMap}
    vmaps::Dict{String,AVertexMap}
end
```

A type storing properties associated to networks.
