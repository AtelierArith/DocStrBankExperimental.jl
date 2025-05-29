```
convex_hull(points::Vector{VN}; [algorithm]=nothing, [backend]=nothing,
            [solver]=nothing) where {N, VN<:AbstractVector{N}}
```

Compute the convex hull of a list of points.

### Input

  * `points`    – list of points
  * `algorithm` – (optional, default: `nothing`) the convex-hull algorithm; see                below for valid options
  * `backend`   – (optional, default: `nothing`) polyhedral computation backend                for higher-dimensional point sets
  * `solver`    – (optional, default: `nothing`) the linear-programming solver                used in the backend

### Output

The convex hull as a list of points.

### Algorithm

A pre-processing step treats the cases with up to two points for one dimension and up to four points for two dimensions. For more points in one resp. two dimensions, we use more general algorithms.

For the one-dimensional case, we return the minimum and maximum points, in that order.

The two-dimensional case is handled with a planar convex-hull algorithm. The following algorithms are available:

  * `"monotone_chain"`        – compute the convex hull of points in the plane                              using Andrew's monotone-chain method
  * `"monotone_chain_sorted"` – the same as `"monotone_chain"` but assuming that                              the points are already sorted in                              counter-clockwise fashion

See the reference docstring of each of those algorithms for details.

The higher-dimensional case is treated using the concrete polyhedra library `Polyhedra`, which gives access to libraries such as `CDDLib` and `ConvexHull.jl`. These libraries can be chosen via the `backend` argument.

### Notes

For the in-place version use `convex_hull!` instead of `convex_hull`.

### Examples

Compute the convex hull of a random set of points:

```jldoctest ch_label
julia> points = [randn(2) for i in 1:30]; # 30 random points in 2D

julia> hull = convex_hull(points);

julia> typeof(hull)
Vector{Vector{Float64}} (alias for Array{Array{Float64, 1}, 1})
```
