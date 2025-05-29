例えば、これは `NucleicAcidSubstitutionModel` のための4です。

```jldoctest
julia> nstates(JC69([0.03], false))
4

julia> nstates(HKY85([.5], [0.25, 0.25, 0.25, 0.25]))
4
```
