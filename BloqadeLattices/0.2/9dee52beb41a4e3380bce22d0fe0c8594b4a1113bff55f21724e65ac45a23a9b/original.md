```
offset_axes(sites::AtomList{D, T}, offsets::Vararg{T,D}) where {D, T}
offset_axes(offsets...)
```

Offset the `sites` by distance specified by `offsets`.

```jldoctest; setup=:(using BloqadeLattices)
julia> sites = AtomList([(1.0, 2.0), (10.0, 3.0), (1.0, 12.0), (3.0, 5.0)])
4-element AtomList{2, Float64}:
 (1.0, 2.0)
 (10.0, 3.0)
 (1.0, 12.0)
 (3.0, 5.0)

julia> offset_axes(sites, 1.0, 3.0)
4-element AtomList{2, Float64}:
 (2.0, 5.0)
 (11.0, 6.0)
 (2.0, 15.0)
 (4.0, 8.0)
```
