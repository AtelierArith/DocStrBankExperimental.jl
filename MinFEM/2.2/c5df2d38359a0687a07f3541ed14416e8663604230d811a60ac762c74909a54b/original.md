```julia
jacobian(
    mesh::MinFEM.Mesh,
    element::Int64
) -> Tuple{Float64, LinearAlgebra.Adjoint{Float64, Matrix{Float64}}}

```

Same as previous `jacobian(...)`, but takes a mesh and an element id as arguments. Extracts coordinates of the support nodes from the mesh and passes them to the base function.
