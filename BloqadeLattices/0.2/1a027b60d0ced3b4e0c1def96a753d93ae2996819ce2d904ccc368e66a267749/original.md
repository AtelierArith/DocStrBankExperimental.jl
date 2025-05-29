```
rescale_axes(sites::AtomList{D, T}, scale::Real) where {D, T}
rescale_axes(scale)
```

Rescale the `sites` by a constant `scale`.

```jldoctest; setup=:(using BloqadeLattices)
julia> sites = AtomList([(1.0, 2.0), (10.0, 3.0), (1.0, 12.0), (3.0, 5.0)])
4-element AtomList{2, Float64}:
 (1.0, 2.0)
 (10.0, 3.0)
 (1.0, 12.0)
 (3.0, 5.0)

julia> rescale_axes(sites, 2.0)
4-element AtomList{2, Float64}:
 (2.0, 4.0)
 (20.0, 6.0)
 (2.0, 24.0)
 (6.0, 10.0)
```
