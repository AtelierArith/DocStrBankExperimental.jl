```julia
Poisson(
    f::Function,
    g::CTFlows.AbstractHamiltonian{TD<:CTFlows.TimeDependence, VD<:CTFlows.VariableDependence}
) -> CTFlows.Hamiltonian

```

Poisson bracket of a function and an Hamiltonian function (subtype of AbstractHamiltonian) : {f, g} = Poisson(f, g)

# Example

```@example
julia> f = (x, p) -> x[2]^2 + 2x[1]^2 + p[1]^2
julia> g = (x, p) -> 3x[2]^2 + -x[1]^2 + p[2]^2 + p[1]
julia> G = Hamiltonian(g)          
julia> Poisson(f, G)([1, 2], [2, 1])
-20
julia> f = (t, x, p, v) -> t*v[1]*x[2]^2 + 2x[1]^2 + p[1]^2 + v[2]
julia> g = (t, x, p, v) -> 3x[2]^2 + -x[1]^2 + p[2]^2 + p[1] + t - v[2]
julia> G = Hamiltonian(g, autonomous=false, variable=true)
julia> Poisson(f, G)(2, [1, 2], [2, 1], [4, 4])
-76
```
