```julia
⋅(
    X::CTFlows.VectorField{<:Function, CTFlows.Autonomous},
    f::Function
) -> CTFlows.var"#27#29"{CTFlows.VectorField{var"#s56", CTFlows.Autonomous, var"#s26"}, <:Function} where {var"#s56"<:Function, var"#s26"<:CTFlows.VariableDependence}

```

Lie derivative of a scalar function along a vector field : L_X(f) = X⋅f, in autonomous case

# Example

```@example
julia> φ = x -> [x[2], -x[1]]
julia> X = VectorField(φ)
julia> f = x -> x[1]^2 + x[2]^2
julia> (X⋅f)([1, 2])
0
```
