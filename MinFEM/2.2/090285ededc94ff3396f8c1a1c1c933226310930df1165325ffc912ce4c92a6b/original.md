```julia
update_mesh!(
    mesh::MinFEM.Mesh,
    c::Vector{Vector{Float64}}
) -> Vector{Vector{Float64}}

```

Updates given mesh by shifting all nodes to new coordinates c.
