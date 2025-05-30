```julia
Lie(
    X::CTFlows.VectorField{<:Function, CTFlows.NonAutonomous, V<:CTFlows.VariableDependence},
    Y::CTFlows.VectorField{<:Function, CTFlows.NonAutonomous, V<:CTFlows.VariableDependence}
) -> Any

```

Lie bracket of two vector fields: [X, Y] = Lie(X, Y), nonautonomous case

# Example

```@example
julia> f = (t, x, v) -> [t + x[2] + v, -2x[1] - v]
julia> g = (t, x, v) -> [t + 3x[2] + v, -x[1] - v]
julia> X = VectorField(f, NonAutonomous, NonFixed)
julia> Y = VectorField(g, NonAutonomous, NonFixed)
julia> Lie(X, Y)(1, [1, 2], 1)
[-7,12]
```
