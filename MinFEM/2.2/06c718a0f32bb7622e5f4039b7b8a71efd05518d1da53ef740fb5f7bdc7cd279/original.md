```julia
jacobian(
    mesh::MinFEM.Mesh,
    nodes::Vector{Int64}
) -> Tuple{Float64, LinearAlgebra.Adjoint{Float64, Matrix{Float64}}}

```

Same as previous `jacobian(...)`, but takes a mesh and set of nodes as arguments. Extracts coordinates from the mesh and passes them to the base function.

Commonly the coordinates correspond to one element in a mesh, but not necessarily have to.
