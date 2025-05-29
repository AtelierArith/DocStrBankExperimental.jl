```
Mesh(vertices)
```

Generate a triangular mesh from a vector of vertices.

# Arguments

  * `vertices`: List of vertices (each vertex implement as `Vec`).

# Returns

A `Mesh` object.

# Example

```jldoctest
julia> verts = [Vec(0.0, 0.0, 0.0), Vec(0.0, 1.0, 0.0), Vec(1.0, 0.0, 0.0)];

julia> Mesh(verts);
```
