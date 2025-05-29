```julia
get_slopes(
    pwl::InfrastructureSystems.PiecewiseLinearData
) -> Vector{Float64}

```

Calculates the slopes of the line segments defined by the PiecewiseLinearData, returning one fewer slope than the number of underlying points.
