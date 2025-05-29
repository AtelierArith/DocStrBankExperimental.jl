```julia
compute_errors(
    anasol::Vector{Float64},
    data::PLaplace.PLaplaceData
) -> Vector{Float64}

```

Same as previous compute_errors(...). However takes discretized analytical solution and PLaplaceData(@ref) as arguments.
