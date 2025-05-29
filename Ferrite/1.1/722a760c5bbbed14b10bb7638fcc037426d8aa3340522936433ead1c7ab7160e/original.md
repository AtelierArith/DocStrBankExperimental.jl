```
addcellset!(grid::AbstractGrid, name::String, cellid::AbstractVecOrSet{Int})
addcellset!(grid::AbstractGrid, name::String, f::function; all::Bool=true)
```

Adds a cellset to the grid with key `name`. Cellsets are typically used to define subdomains of the problem, e.g. two materials in the computational domain. The `DofHandler` can construct different fields which live not on the whole domain, but rather on a cellset. `all=true` implies that `f(x)` must return `true` for all nodal coordinates `x` in the cell if the cell should be added to the set, otherwise it suffices that `f(x)` returns `true` for one node.

```julia
addcellset!(grid, "left", Set((1,3))) #add cells with id 1 and 3 to cellset left
addcellset!(grid, "right", x -> norm(x[1]) < 2.0 ) #add cell to cellset right, if x[1] of each cell's node is smaller than 2.0
```
