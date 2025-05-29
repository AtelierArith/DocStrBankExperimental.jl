```
properties(mesh::Mesh)
```

Retrieve the properties of a mesh. Properties are stored as a dictionary with one entry per type of property. Each property is an array of objects, one per triangle. Each property is identified by a symbol (e.g.).

# Arguments

  * `mesh`: The mesh from which to retrieve the normals.

# Returns

A vector containing the normals of the mesh.

# Example

```jldoctest; output=false
julia> r = Rectangle();

julia> add_property!(r, :absorbed_PAR, [0.0, 0.0]);

julia> properties(r);
```
