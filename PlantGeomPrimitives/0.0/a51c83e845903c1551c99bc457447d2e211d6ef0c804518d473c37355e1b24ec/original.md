```
add!(mesh1, mesh2; kwargs...)
```

Manually add a mesh to an existing mesh with optional properties captured as keywords. Make sure to be consistent with the properties (both meshes should end up with the same lsit of properties). For example, if the scene was created with `:colors``, then you should provide`:colors`` for the new mesh as well.

# Arguments

  * `mesh1`: The current mesh we want to extend.
  * `mesh1`: A new mesh we want to add.
  * `kwargs`: Properties to be set per triangle in the new mesh.

# Example

```jldoctest
julia> t1 = Triangle(length = 1.0, width = 1.0);

julia> using ColorTypes: RGB

julia> add_property!(t1, :colors, rand(RGB));

julia> t2 = Rectangle(length = 5.0, width = 0.5);

julia> add!(t1, t2, colors = rand(RGB));
```
