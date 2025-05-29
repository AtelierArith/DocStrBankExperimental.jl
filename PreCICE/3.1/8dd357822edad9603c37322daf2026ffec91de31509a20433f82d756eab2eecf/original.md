```
setMeshVertices(meshName::String, positions::AbstractArray{Float64})::AbstractArray{Int32,1}
```

Create multiple mesh vertices on a coupling mesh and return an array holding their ids.

# Arguments

  * `meshName::String`: The name of the mesh to add the vertices to.
  * `positions::AbstractArray{Float64}`: An array holding the coordinates of the vertices.                                      It has the shape [N x D] where N = number of vertices and D = dimensions of geometry

# Notes

Previous calls:

  * [`initialize`](@ref) has not yet been called

# See also

[`getDimensions`](@ref), [`setMeshVertex`](@ref)

# Examples

Example for a 3D Problem with 5 vertices

```julia
vertices = [1 1 1;2 2 2;3 3 3]
vertex_ids = setMeshVertices("MeshOne", vertices)
```
