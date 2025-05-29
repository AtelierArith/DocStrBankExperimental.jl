```
area(mesh::Mesh)
```

Total surface area of a mesh (as the sum of areas of individual triangles).

# Arguments

  * `mesh`: Mesh which area is to be calculated.

# Returns

The total surface area of the mesh as a number.

# Example

```jldoctest
julia> r = Rectangle(length = 10.0, width = 0.2);

julia> area(r);

julia> r = Rectangle(length = 10f0, width = 0.2f0);

julia> area(r);
```
