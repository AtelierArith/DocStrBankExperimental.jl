```julia
elementdiameter_boundary(
    mesh::MinFEM.Mesh,
    element::Int64
) -> Union{Float64, Int64}

```

Same as previous `elementdiameter_boundary(...)`, but takes a mesh and a boundary element id as arguments. Extracts coordinates of the support nodes from the mesh and passes them to the base function.
