```julia
jacobian_boundary(
    mesh::MinFEM.Mesh,
    nodes::Vector{Int64}
) -> Union{Nothing, Float64, Int64}

```

Same as previous `jacobian_boundary(...)`, but takes a mesh and set of nodes as arguments. Extracts coordinates from the mesh and passes them to the base function.

Commonly the coordinates correspond to one element in a mesh, but not necessarily have to.
