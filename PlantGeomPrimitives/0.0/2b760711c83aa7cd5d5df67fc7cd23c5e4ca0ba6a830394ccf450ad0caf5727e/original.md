```
areas(m::Mesh)
```

A vector with the areas of the different triangles that form a mesh.

# Arguments

  * `mesh`: Mesh which areas are to be calculated.

# Returns

A vector with the areas of the different triangles that form the mesh.

# Example

```jldoctest
julia> r = Rectangle(length = 10.0, width = 0.2);

julia> areas(r);

julia> r = Rectangle(length = 10f0, width = 0.2f0);

julia> areas(r);
```
