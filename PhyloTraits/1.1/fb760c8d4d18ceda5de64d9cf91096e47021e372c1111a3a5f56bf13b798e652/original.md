For example, this is 4 for a `NucleicAcidSubstitutionModel`.

```jldoctest
julia> nstates(JC69([0.03], false))
4

julia> nstates(HKY85([.5], [0.25, 0.25, 0.25, 0.25]))
4
```
