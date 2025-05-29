```
id_in_position(pos, model::ABM{<:GridSpaceSingle}) → id
```

Return the agent ID in the given position. This will be `0` if there is no agent in this position.

This is similar to [`ids_in_position`](@ref), but specialized for `GridSpaceSingle`. See also [`isempty`](@ref).
