```
get_position(v::VertexModel)
get_position(nw::Network, vidx::VIndex)
```

Returns the `position` metadata of vertex `v`. Might error if not present.

See also: [`has_position`](@ref), [`set_position!`](@ref).
