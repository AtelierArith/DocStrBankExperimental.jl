```
delaunay(dim::Integer, numpoints::Integer, points::AbstractVector,
    [flags::AbstractString]) → Matrix{Int32}
```

Compute the Delaunay triangulation of a cloud of points in an arbitrary dimension `dim`. The vector `points` holds the data in "component major order", i.e., components are consecutive within the vector. The vector `points` therefore must have length `dim * numpoints`.

The returned matrix has shape `(dim + 1, nsimplices)`, where `nsimplices` is the number of simplices in the computed Delaunay triangulation.

You can override the default set of flags that Qhull uses by passing an additional positional `flags` argument. The default set of flags is `qhull d Qt Qbb Qc Qz` for up to 3 dimensions, and `qhull d Qt Qbb Qc Qx` for higher dimensions. The flags you pass override the default flags, i.e. you have to pass all the flags that Qhull should use.

## Example: passing a column-major ordered vector of points

In this case, the dimension and number of points must be specified.

```julia
using MiniQhull
dim          = 2
numpoints    = 4
coordinates  = [0,0,0,1,1,0,1,1]
connectivity = delaunay(dim, numpoints, coordinates)
# output
3×2 Array{Int32,2}:
 4  4
 2  3
 1  1
```

```
delaunay(points::AbstractMatrix, [flags::AbstractString]) -> Matrix{Int32}
```

In this variant, the cloud of points is specified by a matrix with `size(matrix) == (dim, numpoints)`.

## Example: passing a matrix of points

```julia
using MiniQhull
coordinates  = [0 0 1 1; 0 1 0 1]
connectivity = delaunay(coordinates)
# output
3×2 Array{Int32,2}:
 4  4
 2  3
 1  1
```

```
delaunay(points::AbstractVector{T}, [flags::AbstractString]) where T -> Matrix{Int32}
```

In this variant, the cloud of points is specified by a vector of points.

`points` can a `Vector{Vector}` but this is slow, because the data needs to be flattened and collected before passing the data to Qhull.

```julia
pts = [[0.,0.], [0.,1.], [1.,0.], [1.,1.]]
delaunay(pts)
# output
3×2 Array{Int32,2}:
 4  4
 2  3
 1  1
```

A more efficient alternative is of `points` has the same memory layout as a column-major vector, that is, if `T` is some type such that `reinterpret(Float64, points)` yields a column-major vector of the points. This avoids extra memory allocations, and is useful if you have a large number of points to triangulate. Examples are using equal-length tuples or `SVector`s to represent the points.

```julia
using MiniQhull, StaticArrays
dim = 3
npts = 500
pts = [SVector{dim, Float64}(rand(dim)) for i = 1:npts];
flags = "qhull d Qbb Qc QJ Pp" # some custom flags
connectivity = delaunay(pts, flags)
```
