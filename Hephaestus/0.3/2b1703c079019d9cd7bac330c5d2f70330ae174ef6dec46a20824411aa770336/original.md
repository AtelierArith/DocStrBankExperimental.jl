```
node!(model::Model, ID::Int,
    x::Real, y::Real, z::Real;
    u_x::Bool = false, u_y::Bool = false, u_z::Bool = false,
    θ_x::Bool = false, θ_y::Bool = false, θ_z::Bool = false)::Model
```

Add a node to a finite element model.
