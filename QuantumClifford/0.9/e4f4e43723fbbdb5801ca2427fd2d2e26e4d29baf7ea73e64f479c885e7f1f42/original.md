Given an operator, return all operators that have the same tableau but different phases.

```jldoctest
julia> length(collect(enumerate_phases(tCNOT)))
16
```

See also: [`enumerate_cliffords`](@ref), [`clifford_cardinality`](@ref).
