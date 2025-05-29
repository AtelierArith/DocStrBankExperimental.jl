```
ntriangles(mesh)
```

Extract the number of triangles in a mesh.

# Arguments

  * `mesh`: The mesh from which to extract the number of triangles.

# Returns

The number of triangles in the mesh as an integer.

# Example

```jldoctest
julia> v = [Vec(0.0, 0.0, 0.0), Vec(0.0, 1.0, 0.0), Vec(1.0, 0.0, 0.0)];

julia> m = Mesh(v);

julia> ntriangles(m);
```
