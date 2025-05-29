```
vertices(mesh::Mesh)
```

Retrieve the vertices of a mesh.

# Arguments

  * `mesh`: The mesh from which to retrieve the vertices.

# Returns

A vector containing the vertices of the mesh.

# Example

```jldoctest
julia> v = [Vec(0.0, 0.0, 0.0), Vec(0.0, 1.0, 0.0), Vec(1.0, 0.0, 0.0)];

julia> m = Mesh(v);

julia> vertices(m);
```
