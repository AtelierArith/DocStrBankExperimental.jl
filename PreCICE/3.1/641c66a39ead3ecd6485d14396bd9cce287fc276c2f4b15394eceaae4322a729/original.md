```
setMeshTriangles(meshName::String, vertices::AbstractArray{Integer})
```

Set mesh triangle from vertex IDs.

# Arguments

  * `meshName::String`: Name of the mesh to add the edge to.
  * `vertices::AbstractArray{Integer}`: IDs of the vertices of the triangles.

# Examples

Set mesh triangles for a problem with 4 mesh vertices in the form of a square with both diagonals which are fully interconnected.

```julia-repl
julia> vertices = [1 2 3; 1 3 4; 1 2 4; 1 3 4]
julia> vertices.shape
(4,3)
julia> setMeshTriangles("MeshOne", vertices)
```
