```julia
jacobian_boundary(
    mesh::MinFEM.Mesh,
    element::Int64
) -> Union{Nothing, Float64, Int64}

```

Same as previous `jacobian_boundary(...)`, but takes a mesh and an element id as arguments. Extracts coordinates of the support nodes from the mesh and passes them to the base function.
