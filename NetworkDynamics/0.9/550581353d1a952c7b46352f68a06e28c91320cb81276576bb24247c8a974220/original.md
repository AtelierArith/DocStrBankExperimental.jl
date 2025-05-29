```
set_graphelement!(c::EdgeModel, nt::@NamedTuple{src::T, dst::T})
set_graphelement!(c::EdgeModel, p::Pair)
set_graphelement!(c::VertexModel, vidx::Int)
set_graphelement!(nw::Network, idx::Union{VIndex,EIndex}, value)
```

Sets the `graphelement` metadata for the component. For edges this takes a named tuple `(;src, dst)` where both are either integer (vertex index) or symbol (vertex name). For vertices it takes a single integer `vidx`.
