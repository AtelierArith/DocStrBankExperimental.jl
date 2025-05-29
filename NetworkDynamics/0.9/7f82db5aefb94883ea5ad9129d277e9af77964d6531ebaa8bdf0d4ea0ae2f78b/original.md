```
get_graphelement(c::EdgeModel)::@NamedTuple{src::T, dst::T}
get_graphelement(c::VertexModel)::Int
get_graphelement(nw::Network, idx::Union{VIndex,EIndex})
```

Retrieves the `graphelement` metadata for the component model. For edges this returns a named tuple `(;src, dst)` where both are either integers (vertex index) or symbols (vertex name).
