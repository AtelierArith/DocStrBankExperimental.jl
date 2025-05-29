```julia
==(
    compound_1::ChemEquations.Compound,
    compound_2::ChemEquations.Compound
) -> Bool

```

Checks whether two compounds are chemically equal.

# Examples

```jldoctest
julia> cc"MgOHOH" == cc"Mg(OH)2"
true
```
