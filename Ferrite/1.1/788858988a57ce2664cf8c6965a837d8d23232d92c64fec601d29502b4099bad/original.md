```
InterfaceCache(grid::Grid)
InterfaceCache(dh::AbstractDofHandler)
```

Create a cache object with pre-allocated memory for the nodes, coordinates, and dofs of an interface. The cache is updated for a new cell by calling `reinit!(cache, facet_a, facet_b)` where `facet_a::FacetIndex` and `facet_b::FacetIndex` are the two interface facets.

**Struct fields of `InterfaceCache`**

  * `ic.a :: FacetCache`: facet cache for the first facet of the interface
  * `ic.b :: FacetCache`: facet cache for the second facet of the interface
  * `ic.dofs :: Vector{Int}`: global dof ids for the interface (union of `ic.a.dofs` and `ic.b.dofs`)

**Methods with `InterfaceCache`**

  * `reinit!(cache::InterfaceCache, facet_a::FacetIndex, facet_b::FacetIndex)`: reinitialize the cache for a new interface
  * `interfacedofs(ic)`: get the global dof ids of the interface

See also [`InterfaceIterator`](@ref).
