```
MC(vol::Array{F,3}, I::Type = Int; x = [], y = [], z = [])
```

# Description

Structure to hold temporaries and output of the marching cubes algorithm. Vertices, normals and triangles are accessible using `m.vertices`, `m.normals` and `m.triangles`. 1-based indexing is assumed. Optionally, pass `x`, `y`, `z` to normalize the vertices coordinates instead of `0:nx-1`, `0:ny-1` and `0:nz-1`.

# Arguments

```
- `vol`: rank 3 array of floats (volume) on which the Marching Cubes algorithm is applied.
- `I`: Int32, Int64, ...: vertices / normals / triangles index `Integer` type (defaults to `Int`).
- `x` normalize vertex.x to the coordinates of `x`.
- `y` normalize vertex.y to the coordinates of `y`.
- `z` normalize vertex.z to the coordinates of `z`.
```
