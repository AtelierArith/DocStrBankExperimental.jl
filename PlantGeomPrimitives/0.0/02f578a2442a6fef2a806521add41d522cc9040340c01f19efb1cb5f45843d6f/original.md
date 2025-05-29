```
normals(mesh::Mesh)
```

Retrieve the normals of a mesh.

# Arguments

  * `mesh`: The mesh from which to retrieve the normals.

# Returns

A vector containing the normals of the mesh.

# Example

```jldoctest; output=false
julia> v = [Vec(0.0, 0.0, 0.0), Vec(0.0, 1.0, 0.0), Vec(1.0, 0.0, 0.0)];

julia> m = Mesh(v);

julia> normals(m);
```
