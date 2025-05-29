```julia
spherical2cartesian(
    r::Number,
    θ::Number,
    ϕ::Number
) -> Union{PhysicalParticles.PVector, PhysicalParticles.PVector2D}

```

球面座標を `PVector` に変換します。
