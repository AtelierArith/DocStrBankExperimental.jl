```
halo(ent::GeometryEntity{T}, outer_delta, inner_delta=nothing)
```

Return the "halo" of `ent` using an offset of `outer_delta`.

By default, the halo is a vector containing [`offset(footprint(ent), outer_delta)`](@ref), but it may contain any number of `GeometryEntity`s that together fully cover `ent` with a margin of `outer_delta`. It is not guaranteed to cover [`footprint(ent)`](@ref).

If `inner_delta` is provided, then the offset at `inner_delta` is subtracted from the result.

A `GeometryEntity` should implement a specialized `halo` if there is an efficient non-`Polygon` representation of the halo. If it does not, then by default `offset` will be used, which first resolves the entity into `Polygon`s using `to_polygons`.
