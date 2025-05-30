```julia
Poisson(
    f::CTFlows.AbstractHamiltonian{CTFlows.NonAutonomous, V<:CTFlows.VariableDependence},
    g::CTFlows.AbstractHamiltonian{CTFlows.NonAutonomous, V<:CTFlows.VariableDependence}
) -> Any

```

2つのハミルトニアン関数（AbstractHamiltonianのサブタイプ）のポアソン括弧 : {f, g} = Poisson(f, g)、非自律的な場合

# 例

```@example
julia> f = (t, x, p, v) -> t*v[1]*x[2]^2 + 2x[1]^2 + p[1]^2 + v[2]
julia> g = (t, x, p, v) -> 3x[2]^2 + -x[1]^2 + p[2]^2 + p[1] + t - v[2]
julia> F = Hamiltonian(f, autonomous=false, variable=true)
julia> G = Hamiltonian(g, autonomous=false, variable=true)
julia> Poisson(F, G)(2, [1, 2], [2, 1], [4, 4])
-76
julia> Poisson(f, g, NonAutonomous, NonFixed)(2, [1, 2], [2, 1], [4, 4])
-76
```
