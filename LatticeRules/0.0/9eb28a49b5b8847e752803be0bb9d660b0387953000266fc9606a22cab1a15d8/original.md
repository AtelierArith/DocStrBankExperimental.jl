```
ShiftedLatticeRule32(lattice_rule)
ShiftedLatticeRule32(lattice_rule, shift)
```

Returns a shifted rank-1 lattice rule based on the lattice rule `lattice_rule` using the random shift `shift`. If no random shift is provided, we use `shift = rand(length(lattice_rule))`.

# Examples

```jldoctest; setup = :(using LatticeRules; import Random; Random.seed!(1))
julia> lattice_rule = LatticeRule32(16)
LatticeRule32{16}

julia> shifted_lattice_rule = ShiftedLatticeRule32(lattice_rule)
ShiftedLatticeRule32{16}

julia> getpoint(shifted_lattice_rule, 0)
16-element Array{Float64,1}:
 0.23603334566204692
 0.34651701419196046
 0.3127069683360675
 0.00790928339056074
 0.4886128300795012
 0.21096820215853596
 0.951916339835734
 0.9999046588986136
 0.25166218303197185
 0.9866663668987996
 0.5557510873245723
 0.43710797460962514
 0.42471785049513144
 0.773223048457377
 0.2811902322857298
 0.20947237319807077

```

See also: [`LatticeRule32`](@ref), [`getpoint`](@ref)
