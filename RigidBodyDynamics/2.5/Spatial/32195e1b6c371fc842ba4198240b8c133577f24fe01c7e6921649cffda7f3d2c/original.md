```julia
struct FreeVector3D{V<:(AbstractVector)}
```

A `FreeVector3D` represents a [free vector](https://en.wikipedia.org/wiki/Euclidean_vector#Overview).

Examples of free vectors include displacements and velocities of points.

Applying a `Transform3D` to a `FreeVector3D` only rotates the `FreeVector3D`.
