```julia
Lie(
    X::CTFlows.VectorField{<:Function, CTFlows.Autonomous, V<:CTFlows.VariableDependence},
    Y::CTFlows.VectorField{<:Function, CTFlows.Autonomous, V<:CTFlows.VariableDependence}
) -> Any

```

二つのベクトル場のリーブラケット: [X, Y] = Lie(X, Y), 自律的な場合

# 例

```@example
julia> f = x -> [x[2], 2x[1]]
julia> g = x -> [3x[2], -x[1]]
julia> X = VectorField(f)
julia> Y = VectorField(g)
julia> Lie(X, Y)([1, 2])
[7, -14]
```
