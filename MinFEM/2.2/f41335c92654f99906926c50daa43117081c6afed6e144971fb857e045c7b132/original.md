```julia
elementdiameter(
    mesh::MinFEM.Mesh,
    nodes::Vector{Int64}
) -> Union{Float64, Int64}

```

Same as previous `elementdiameter(...)`, but takes a mesh and set of nodes as arguments. Extracts coordinates from the mesh and passes them to the base function.

Commonly the coordinates correspond to one (boundary) element in a mesh, but not necessarily have to.
