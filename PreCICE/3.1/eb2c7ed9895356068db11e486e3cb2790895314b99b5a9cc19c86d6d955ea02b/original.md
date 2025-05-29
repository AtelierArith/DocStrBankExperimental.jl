```
setMeshEdges(meshName::String, vertices::AbstractArray{Cint})
```

Create multiple mesh edges

# Arguments

  * `meshName::String`: Name of the mesh to add the edge to.
  * `vertices::AbstractArray{Cint}`: An array holding the vertex IDs of the edges.                                  It has the shape [N x 2] where N = number of edges.

# Examples

Set mesh edges for a problem with 4 mesh vertices in the form of a square with both diagonals which are fully interconnected.

```julia-repl
julia> vertices = [1 2; 1 3; 1 4; 2 3; 2 4; 3 4]
julia> vertices.shape
(6,2)
julia> setMeshEdges("MeshOne", vertices)
```
