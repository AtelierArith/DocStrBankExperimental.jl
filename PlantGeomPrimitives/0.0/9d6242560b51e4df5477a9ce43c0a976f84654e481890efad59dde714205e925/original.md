```
add_property!(m::Mesh, prop::Symbol, data, nt = ntriangles(m))
```

Add a property to a mesh. The property is identified by a name (`prop`) and is stored as an array of values (`data`), one per triangle. If the property already exists, the new data is appended to the existing property, otherwise a new property is created. It is possible to pass a single object for `data`, in which case the property will be set to the same value for all triangles.

# Arguments

  * `mesh`: The mesh to which the property is to be added.
  * `prop`: The name of the property to be added as a `Symbol`.
  * `data`: The data to be added to the property (an array or a single value).
  * `nt`: The number of triangles to be assumed if `data` is not an array. By default this is the number of triangles in the mesh.

# Returns

The mesh with updated properties.

# Example

```jldoctest
julia> r = Rectangle();

julia> add_property!(r, :absorbed_PAR, [0.0, 0.0]);
```
