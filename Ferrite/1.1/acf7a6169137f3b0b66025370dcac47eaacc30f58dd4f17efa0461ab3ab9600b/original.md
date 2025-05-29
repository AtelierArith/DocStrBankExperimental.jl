```
addfacetset!(grid::AbstractGrid, name::String, faceid::AbstractVecOrSet{FacetIndex})
addfacetset!(grid::AbstractGrid, name::String, f::Function; all::Bool=true)
```

Adds a facetset to the grid with key `name`. A facetset maps a `String` key to a `OrderedSet` of tuples corresponding to `(global_cell_id, local_facet_id)`. Facetsets can be used to initialize `Dirichlet` boundary conditions for the `ConstraintHandler`. `all=true` implies that `f(x)` must return `true` for all nodal coordinates `x` on the facet if the facet should be added to the set, otherwise it suffices that `f(x)` returns `true` for one node.

```julia
addfacetset!(grid, "right", Set((FacetIndex(2,2), FacetIndex(4,2)))) #see grid manual example for reference
addfacetset!(grid, "clamped", x -> norm(x[1]) ≈ 0.0) #see incompressible elasticity example for reference
```
