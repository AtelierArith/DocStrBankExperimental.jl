addboundaryfacetset!(grid::AbstractGrid, topology::ExclusiveTopology, name::String, f::Function; all::Bool=true)

Adds a boundary facetset to the grid with key `name`. A facetset maps a `String` key to a `OrderedSet` of tuples corresponding to `(global_cell_id, local_facet_id)`. Facetsets are used to initialize `Dirichlet` structs, that are needed to specify the boundary for the `ConstraintHandler`. `all=true` implies that `f(x)` must return `true` for all nodal coordinates `x` on the facet if the facet should be added to the set, otherwise it suffices that `f(x)` returns `true` for one node.
