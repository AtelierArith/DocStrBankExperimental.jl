```
PointEvalHandler(grid::Grid, points::AbstractVector{Vec{dim,T}}; kwargs...) where {dim, T}
```

The `PointEvalHandler` can be used for function evaluation in *arbitrary points* in the domain – not just in quadrature points or nodes.

The constructor takes a grid and a vector of coordinates for the points. The `PointEvalHandler` computes i) the corresponding cell, and ii) the (local) coordinate within the cell, for each point. The fields of the `PointEvalHandler` are:

  * `cells::Vector{Union{Int,Nothing}}`: vector with cell IDs for the points, with `nothing` for points that could not be found.
  * `local_coords::Vector{Union{Vec,Nothing}}`: vector with the local coordinates (i.e. coordinates in the reference configuration) for the points, with `nothing` for points that could not be found.

There are two ways to use the `PointEvalHandler` to evaluate functions:

  * [`evaluate_at_points`](@ref): can be used when the function is described by i) a `dh::DofHandler` + `uh::Vector` (for example the FE-solution), or ii) a `p::L2Projector` + `ph::Vector` (for projected data).
  * Iteration with [`PointIterator`](@ref) + [`PointValues`](@ref): can be used for more flexible evaluation in the points, for example to compute gradients.
