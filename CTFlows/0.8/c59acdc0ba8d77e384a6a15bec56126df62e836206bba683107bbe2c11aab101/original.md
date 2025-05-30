```julia
Poisson(
    f::CTFlows.AbstractHamiltonian{TD<:CTFlows.TimeDependence, VD<:CTFlows.VariableDependence},
    g::Function
) -> CTFlows.Hamiltonian

```

Poisson bracket of an Hamiltonian function (subtype of AbstractHamiltonian) and a function : {f, g} = Poisson(f, g), autonomous case

# Example

```@example
julia> f = (x, p) -> x[2]^2 + 2x[1]^2 + p[1]^2
julia> g = (x, p) -> 3x[2]^2 + -x[1]^2 + p[2]^2 + p[1]
julia> F = Hamiltonian(f)
julia> Poisson(F, g)([1, 2], [2, 1])
-20
julia> f = (t, x, p, v) -> t*v[1]*x[2]^2 + 2x[1]^2 + p[1]^2 + v[2]
julia> g = (t, x, p, v) -> 3x[2]^2 + -x[1]^2 + p[2]^2 + p[1] + t - v[2]
julia> F = Hamiltonian(f, autonomous=false, variable=true)
julia> Poisson(F, g)(2, [1, 2], [2, 1], [4, 4])
-76
```
