```julia
Lift(
    X::CTFlows.VectorField
) -> CTFlows.HamiltonianLift{CTFlows.VectorField{TF, TD, VD}} where {TF<:Function, TD<:CTFlows.TimeDependence, VD<:CTFlows.VariableDependence}

```

ベクトル場のハミルトンリフトを返します。

# 例

```@example
julia> HL = Lift(VectorField(x -> [x[1]^2,x[2]^2], autonomous=true, variable=false))
julia> HL([1, 0], [0, 1])
0
julia> HL = Lift(VectorField((t, x, v) -> [t+x[1]^2,x[2]^2+v], autonomous=false, variable=true))
julia> HL(1, [1, 0], [0, 1], 1)
1
julia> H = Lift(x -> 2x)
julia> H(1, 1)
2
julia> H = Lift((t, x, v) -> 2x + t - v, autonomous=false, variable=true)
julia> H(1, 1, 1, 1)
2
julia> H = Lift((t, x, v) -> 2x + t - v, NonAutonomous, NonFixed)
julia> H(1, 1, 1, 1)
2
```
