```julia
⋅(
    X::CTFlows.VectorField{<:Function, CTFlows.Autonomous},
    f::Function
) -> CTFlows.var"#27#29"{CTFlows.VectorField{var"#s56", CTFlows.Autonomous, var"#s26"}, <:Function} where {var"#s56"<:Function, var"#s26"<:CTFlows.VariableDependence}

スカラー関数のリーベクトル場に沿った導関数 : L_X(f) = X⋅f, 自律的な場合

# 例

```

@example julia> φ = x -> [x[2], -x[1]] julia> X = VectorField(φ) julia> f = x -> x[1]^2 + x[2]^2 julia> (X⋅f)([1, 2]) 0 ```
