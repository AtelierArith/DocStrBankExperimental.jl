```julia
elementdiameter(
    mesh::MinFEM.Mesh,
    element::Int64
) -> Union{Float64, Int64}

```

Same as previous `elementdiameter(...)`, but takes a mesh and an element id as arguments. Extracts coordinates of the support nodes from the mesh and passes them to the base function.
