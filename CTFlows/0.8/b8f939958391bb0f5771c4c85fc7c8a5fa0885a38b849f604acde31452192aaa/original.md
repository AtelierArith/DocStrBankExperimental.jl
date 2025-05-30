```julia
⋅(
    X::CTFlows.VectorField{<:Function, CTFlows.NonAutonomous},
    f::Function
) -> CTFlows.var"#31#33"{CTFlows.VectorField{var"#s57", CTFlows.NonAutonomous, var"#s56"}, <:Function} where {var"#s57"<:Function, var"#s56"<:CTFlows.VariableDependence}

```

Lie derivative of a scalar function along a vector field : L_X(f) = X⋅f, in nonautonomous case

# Example

```@example
julia> φ = (t, x, v) -> [t + x[2] + v[1], -x[1] + v[2]]
julia> X = VectorField(φ, NonAutonomous, NonFixed)
julia> f = (t, x, v) -> t + x[1]^2 + x[2]^2
julia> (X⋅f)(1, [1, 2], [2, 1])
10
```
