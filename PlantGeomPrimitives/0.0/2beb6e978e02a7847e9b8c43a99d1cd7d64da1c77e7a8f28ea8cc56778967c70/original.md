```
Mesh
```

A struct representing a 3D mesh. Every three vertices represents a triangle. Properties per     triangle are stored in a dictionary of arrays.

# Fields

  * `vertices`: A vector containing the vertices of the mesh.
  * `properties`: A dictionary containing additional properties of the mesh (arrays of properties per triangle).

# Example

```jldoctest
julia> v = [Vec(0.0, 0.0, 0.0), Vec(0.0, 1.0, 0.0), Vec(1.0, 0.0, 0.0)];

julia> p = Dict{Symbol, AbstractVector}(:normal => [Vec(0.0, 0.0, 1.0)]);

julia> m = Mesh(v, p);
```
