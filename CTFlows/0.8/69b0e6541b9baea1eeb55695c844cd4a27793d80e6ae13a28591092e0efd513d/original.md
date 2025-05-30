```julia
Lie(
    X::CTFlows.VectorField{<:Function, CTFlows.Autonomous, V<:CTFlows.VariableDependence},
    Y::CTFlows.VectorField{<:Function, CTFlows.Autonomous, V<:CTFlows.VariableDependence}
) -> Any

```

Lie bracket of two vector fields: [X, Y] = Lie(X, Y), autonomous case

# Example

```@example
julia> f = x -> [x[2], 2x[1]]
julia> g = x -> [3x[2], -x[1]]
julia> X = VectorField(f)
julia> Y = VectorField(g)
julia> Lie(X, Y)([1, 2])
[7, -14]
```
