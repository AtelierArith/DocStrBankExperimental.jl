```
SimpleMesh(vertices, topology)
```

A simple mesh with `vertices` and `topology`.

```
SimpleMesh(vertices, connectivities; relations=false)
```

Alternatively, construct a simple mesh with `vertices` and `connectivities`. The option `relations` can be used to build topological relations assuming that the `connectivities` represent the elements of the mesh.

## Examples

```julia
julia> points = [(0.0, 0.0),(1.0, 0.0), (1.0, 1.0)]
julia> connec = [connect((1,2,3))]
julia> mesh   = SimpleMesh(points, connec)
```

See also [`Topology`](@ref), [`GridTopology`](@ref), [`HalfEdgeTopology`](@ref), [`SimpleTopology`](@ref).

### Notes

The option `relations=true` changes the underlying topology of the mesh to a [`HalfEdgeTopology`](@ref) instead of a [`SimpleTopology`](@ref).
