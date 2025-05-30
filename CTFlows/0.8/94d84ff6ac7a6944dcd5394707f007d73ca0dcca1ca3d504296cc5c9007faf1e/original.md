```julia
Poisson(
    f::CTFlows.AbstractHamiltonian{CTFlows.Autonomous, V<:CTFlows.VariableDependence},
    g::CTFlows.AbstractHamiltonian{CTFlows.Autonomous, V<:CTFlows.VariableDependence}
) -> Any

```

Poisson bracket of two Hamiltonian functions (subtype of AbstractHamiltonian) : {f, g} = Poisson(f, g), autonomous case

# Example

```@example
julia> f = (x, p) -> x[2]^2 + 2x[1]^2 + p[1]^2
julia> g = (x, p) -> 3x[2]^2 + -x[1]^2 + p[2]^2 + p[1]
julia> F = Hamiltonian(f)
julia> G = Hamiltonian(g)
julia> Poisson(f, g)([1, 2], [2, 1])
-20            
julia> Poisson(f, G)([1, 2], [2, 1])
-20
julia> Poisson(F, g)([1, 2], [2, 1])
-20
```
