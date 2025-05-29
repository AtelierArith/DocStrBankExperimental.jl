```julia
elementdiameter_boundary(
    mesh::MinFEM.Mesh,
    nodes::Vector{Int64}
) -> Union{Float64, Int64}

```

Same as previous `elementdiameter_boundary(...)`, but takes a mesh and set of nodes as arguments. Extracts coordinates from the mesh and passes them to the base function.

Commonly the coordinates correspond to one (boundary) element in a mesh, but not necessarily have to.

Since the number of nodes to span an element is not prescribed, the functionality is identical to `elementdiameter(args)`. However this function is kept for consistency and improved readability.
