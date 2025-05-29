```julia
struct JablonowskiWilliamsonParams
    η₀::Float64
    σ_tropopause::Float64
    u₀::Float64
    ΔT::Float64
    Tmin::Float64
end

function JablonowskiWilliamsonParams()
    return JablonowskiWilliamsonParams(0.0, 0.5, 30.0, 4.8e5, 200.0)
end
```
