```
Mesh(nt, type)
```

Generate a triangular dense mesh with enough memory allocated to store `nt` triangles. The behaviour is equivalent to generating an empty mesh but may be computationally more efficient when appending a large number of primitives. If a lower floating precision is required, this may be specified as an optional third argument as in `Mesh(10, Float32)`.

# Arguments

  * `nt`: The number of triangles to allocate memory for.
  * `type`: The floating-point precision type for the mesh data (default is `Float64`).

# Returns

A `Mesh` object with no vertices or normals.

# Example

```jldoctest
julia> m = Mesh(1_000);

julia> nvertices(m);

julia> ntriangles(m);

julia> Mesh(1_000, Float32);
```
