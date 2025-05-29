```
nvertices(mesh)
```

The number of vertices in a mesh.

# Arguments

  * `mesh`: The mesh from which to retrieve the number of vertices.

# Returns

The number of vertices in the mesh as an integer.

# Example

```jldoctest
julia> v = [Vec(0.0, 0.0, 0.0), Vec(0.0, 1.0, 0.0), Vec(1.0, 0.0, 0.0)];

julia> m = Mesh(v);

julia> nvertices(m);
```
