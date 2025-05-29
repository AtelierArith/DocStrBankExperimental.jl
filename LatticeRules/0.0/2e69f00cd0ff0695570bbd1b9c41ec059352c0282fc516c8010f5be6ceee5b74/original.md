```
getpoint(lattice_rule, k)
```

Get the `k`-th point of the lattice rule `lattice_rule`.

!!! note
    An alternative syntax is `getindex(lattice_rule, k)` or `lattice_rule[k]`, this allows you to write the one-liner `Q = mean(f.(lattice_rule[0:N-1]))` for the quasi-Monte Carlo estimator for $E[f]$.


```jldoctest; setup = :(using LatticeRules)
julia> lattice_rule = LatticeRule32(2)
LatticeRule32{2}

julia> getpoint(lattice_rule, 3)
2-element Array{Float64,1}:
 0.75
 0.25

```

See also: [`LatticeRule32`](@ref), [`ShiftedLatticeRule32`](@ref)
