```
setMeshVertex(meshName::String, position::AbstractArray{Float64})::Integer
```

Create a mesh vertex on a coupling mesh and return its id.

# Arguments

  * `meshName::String`: The name of the mesh to add the vertex to.
  * `position::AbstractArray{Float64}`: An array with the coordinates of the vertex. Depending on the dimension, either [x1, x2] or [x1,x2,x3].

# Notes

Previous calls:

  * Count of available elements at position matches the configured dimension.

# Examples

```julia
v1_id = setMeshVertex(mesh_name, [1,1,1])
```
