addboundaryvertexset!(grid::AbstractGrid, topology::ExclusiveTopology, name::String, f::Function; all::Bool=true)

Adds a boundary vertexset to the grid with key `name`. A vertexset maps a `String` key to an `OrderedSet` of tuples corresponding to `(global_cell_id, local_vertex_id)`. `all=true` implies that `f(x)` must return `true` for all nodal coordinates `x` on the facet if the facet should be added to the set, otherwise it suffices that `f(x)` returns `true` for one node.
