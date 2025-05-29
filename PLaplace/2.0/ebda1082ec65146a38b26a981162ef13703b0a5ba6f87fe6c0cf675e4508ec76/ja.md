```julia
compute_errors(
    anasol::Vector{Float64},
    data::PLaplace.PLaplaceData
) -> Vector{Float64}

```

前のcompute_errors(...)と同様です。ただし、離散化された解析解とPLaplaceData(@ref)を引数として取ります。
