```julia
PseudoFamily(
    identifier::AbstractString
) -> PseudoPotentialData.PseudoFamily

```

Construction of a PseudoFamily from a `identifier` representing the pseudopotential family to use. For a list of valid identifier, see [`family_identifiers`](@ref). A `PseudoFamily` is an `AbstractDict{Symbol,String} mapping from an element symbol to the full path of the pseudopotential file.
