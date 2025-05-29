```julia
struct Point3D{V<:(AbstractVector)}
```

A `Point3D` represents a position in a given coordinate system.

A `Point3D` is a [bound vector](https://en.wikipedia.org/wiki/Euclidean_vector#Overview). Applying a `Transform3D` to a `Point3D` both rotates and translates the `Point3D`.
