```
optionpool(card::Card)
optionpool(T::Type{<:Card})
```

Return the allowed options for a `Card` or a `Card` type.

# Examples

```jldoctest
julia> optionpool(AtomicPositionsCard)
("alat", "bohr", "angstrom", "crystal", "crystal_sg")

julia> optionpool(CellParametersCard)
("alat", "bohr", "angstrom")

julia> optionpool(SpecialPointsCard)
("tpiba", "crystal", "tpiba_b", "crystal_b", "tpiba_c", "crystal_c")
```
