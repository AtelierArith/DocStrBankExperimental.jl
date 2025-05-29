Given a set of operators, return all operators that have the same tableaux but different phases.

```jldoctest
julia> length(collect(enumerate_phases(enumerate_cliffords(2))))
11520
```

See also: [`enumerate_cliffords`](@ref), [`clifford_cardinality`](@ref).
