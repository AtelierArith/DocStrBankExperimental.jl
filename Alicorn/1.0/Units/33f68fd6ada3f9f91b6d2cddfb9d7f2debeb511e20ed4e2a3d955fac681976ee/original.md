```
listUnitPrefixes(unitCatalogue::UnitCatalogue)
```

Return a dictionary indexing the [`UnitPrefix`](@ref) objects stored in `unitCatalogue` by their name.

# Example

```jldoctest
julia> ucat = UnitCatalogue() ;

julia> prefixes = listUnitPrefixes(ucat) ;

julia> prefixes["micro"]
UnitPrefix micro (μ) of value 1e-6
```
