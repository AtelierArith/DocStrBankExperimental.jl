```
struct Boundary{Dim, M, CRS}
```

A container type for the computational domain within which Ulam's method is applied.

The boundary has dimension `Dim` embedded in manifold `M` with coordinate reference system `CRS`.

The boundary is partitioned according to an [`BinningAlgorithm`](@ref).

### Fields

  * `boundary`: A `Polytope` defining the boundary.

### Methods

```
points(boundary)
```

Calculate a `Dim x N` matrix of boundary vertices.

### 1D Constructors

```
Boundary(x_start, x_end)
```

The boundary is a continuous line segment `Segment` between `x_start` and `x_end`.

### 2D Constructors

```
Boundary(verts)
```

The boundary is a closed polygon `Ngon` with vertices `verts`, which should be be a vector of `(x, y)` coordinates or a `2 x N` matrix.

```
Boundary(xmin, xmax, ymin, ymax)
```

A convenience constructor is also provided for the case of a rectangular boundary.

### ≥3D Constructors

```
Boundary(corner_min, corner_max)
```

The boundary is a `HyperRectangle` with minimum and maximum vertices `corner_min`, `corner_max` where the corners are `NTuple`s, `(x_min, y_min, z_min, ...)`, `(x_max, y_max, z_max, ...)`.

### Automatric Boundary Construction

```
AutoBoundary(traj; nirvana = 0.10)
```

Construct a rectangular boundary in arbitrary dimensions based on the [`Trajectories`](@ref) in `traj`.

The boundary is placed such that a fraction `nirvana` of the data is in nirvana. For example, with the default  value of `0.10`, roughly `10%` of all of the datapoints (split between `x0` and `xT`) will be outside the boundary with  a roughly equal amount on each side.

The shape of the boundary can be further controlled by providing `nirvana` as a vector of length `Dim` of tuples of the form `(min, max)` such  that a fraction `min` (respectively `max`) will be "below" (respectively "above") the boundary along each dimension. 

```
AutoBoundary2D(traj; nirvana = 0.10, tol = 0.001)
```

Construct a tight boundary in two dimensions based on the [`Trajectories`](@ref) in `traj`.

The boundary in question is formed by scaling the convex hull of the trajectory data until a fraction `nirvana` of  the data are bouside the boundary to within `tol` percent. 
