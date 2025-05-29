```
InterfaceIterator(grid::Grid, [topology::ExclusiveTopology])
InterfaceIterator(dh::AbstractDofHandler, [topology::ExclusiveTopology])
```

Create an `InterfaceIterator` to conveniently iterate over all the interfaces in a grid. The elements of the iterator are [`InterfaceCache`](@ref)s which are properly `reinit!`ialized. See [`InterfaceCache`](@ref) for more details. Looping over an `InterfaceIterator`, i.e.:

```julia
for ic in InterfaceIterator(grid, topology)
    # ...
end
```

is thus simply convenience for the following equivalent snippet for grids of dimensions > 1:

```julia
ic = InterfaceCache(grid)
neighborhood = Ferrite.get_facet_facet_neighborhood(topology, grid)
for facet in facetskeleton(topology, grid)
    neighbors = neighborhood[facet[1], facet[2]]
    isempty(neighbors) && continue
    neighbor_facet = neighbors[1]
    reinit!(ic, facet, neighbor_facet)
    # ...
end
```

!!! warning
    `InterfaceIterator` is stateful and should not be used for things other than `for`-looping (e.g. broadcasting over, or collecting the iterator may yield unexpected results).

