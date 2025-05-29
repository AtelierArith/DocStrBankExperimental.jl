```
topoconvert(T, mesh)
```

Convert underlying topology of the `mesh` to topology of type `T`.

## Examples

Convert underlying topology to [`HalfEdgeTopology`](@ref) for efficient topological relations.

```julia
newmesh = topoconvert(HalfEdgeTopology, mesh)
```
