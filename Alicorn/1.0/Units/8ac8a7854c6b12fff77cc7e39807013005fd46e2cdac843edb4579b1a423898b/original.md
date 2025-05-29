```
listBaseUnits(unitCatalogue::UnitCatalogue)
```

Return a dictionary indexing the [`BaseUnit`](@ref) objects stored in `unitCatalogue` by their name.

# Example

```jldoctest
julia> ucat = UnitCatalogue() ;

julia> baseUnits = listBaseUnits(ucat) ;

julia> baseUnits["siemens"]
BaseUnit siemens (1 S = 1 kg^-1 m^-2 s^3 A^2)
```
