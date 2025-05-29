```
get_marker(v::VertexModel)
get_marker(nw::Network, vidx::VIndex)
```

Returns the `marker` metadata of vertex `v`. Might error if not present.

See also: [`has_marker`](@ref), [`set_marker!`](@ref).
