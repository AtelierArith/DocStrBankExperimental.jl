```julia
Poisson(
    f::CTFlows.HamiltonianLift{T<:CTFlows.TimeDependence, V<:CTFlows.VariableDependence},
    g::CTFlows.HamiltonianLift{T<:CTFlows.TimeDependence, V<:CTFlows.VariableDependence}
)

```

Poisson bracket of two HamiltonianLift functions : {f, g} = Poisson(f, g)

# Example

```@example
julia> f = x -> [x[1]^2+x[2]^2, 2x[1]^2]
julia> g = x -> [3x[2]^2, x[2]-x[1]^2]
julia> F = Lift(f)
julia> G = Lift(g)
julia> Poisson(F, G)([1, 2], [2, 1])
-64
julia> f = (t, x, v) -> [t*v[1]*x[2]^2, 2x[1]^2 + + v[2]]
julia> g = (t, x, v) -> [3x[2]^2 + -x[1]^2, t - v[2]]
julia> F = Lift(f, NonAutonomous, NonFixed)
julia> G = Lift(g, NonAutonomous, NonFixed)
julia> Poisson(F, G)(2, [1, 2], [2, 1], [4, 4])
100
```
