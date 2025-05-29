```julia
compute_errors(
    anasol::Vector{Float64},
    numsol::Vector{Float64},
    mesh::MinFEM.Mesh,
    neumann_boundary::Union{Missing, Set{Int64}, Set{MinFEM.Boundary}},
    h::Union{Missing, AbstractVector{Float64}},
    f::Union{Missing, AbstractVector{Float64}},
    p::Float64,
    qdim::Int64
) -> Vector{Float64}

```

Returns various errors of numerical solution compared to given  discretized analytical solution.  First value is error in difference in objective value, then pointwise error L1, L2 and LInf norm.

Intended to be called via a wrapper to ensure the discretized analytical solution and the numerical solution match the mesh.
