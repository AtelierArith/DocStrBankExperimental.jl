```julia
Lie(
    X::Function,
    f::Function;
    autonomous,
    variable
) -> Union{CTFlows.var"#27#29"{CTFlows.VectorField{var"#s56", CTFlows.Autonomous, var"#s26"}, <:Function} where {var"#s56"<:Function, var"#s26"<:CTFlows.VariableDependence}, CTFlows.var"#31#33"{CTFlows.VectorField{var"#s57", CTFlows.NonAutonomous, var"#s56"}, <:Function} where {var"#s57"<:Function, var"#s56"<:CTFlows.VariableDependence}}

```

スカラー関数に沿ったLie微分。依存関係はブール値 : autonomous と variable で指定されます。

# 例

```@example
julia> φ = x -> [x[2], -x[1]]
julia> f = x -> x[1]^2 + x[2]^2
julia> Lie(φ,f)([1, 2])
0
julia> φ = (t, x, v) -> [t + x[2] + v[1], -x[1] + v[2]]
julia> f = (t, x, v) -> t + x[1]^2 + x[2]^2
julia> Lie(φ, f, autonomous=false, variable=true)(1, [1, 2], [2, 1])
10
```
