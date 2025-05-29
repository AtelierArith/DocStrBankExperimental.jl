```
Naive(tris::Vector{Triangle{FT}}, ids::Vector{Int}, rule) where {FT}
```

Wrap the scene into a global bounding box (no acceleration), given the triangles in a scene, the ids linking each triangle to the corresponding material objects. The argument `rule` is left for compatibility with `BVH`, it does not do anything.

## Examples

```jldoctest
julia> using PlantGeomPrimitives

julia> tris = PlantRayTracer.Triangle(Ellipse());

julia> ids  = repeat([1], length(tris));

julia> Naive(tris, ids);
```
