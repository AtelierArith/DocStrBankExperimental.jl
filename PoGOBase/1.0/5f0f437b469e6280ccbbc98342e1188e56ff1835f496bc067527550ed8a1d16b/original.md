```
lineage_ids(poke::Pokemon) → ids
lineage_ids(species::Species) → ids
lineage_ids(list) → ids
```

Return the further evolutions of `poke` or `species` as a list of IDs.

# Examples

```jldoctest
julia> PoGOBase.lineage_ids(only_pokemon("ivysaur"))
2-element Vector{String}:
 "IVYSAUR"
 "VENUSAUR"

julia> PoGOBase.lineage_ids(only_pokemon("ralts"))
4-element Vector{String}:
 "GALLADE"
 "GARDEVOIR"
 "KIRLIA"
 "RALTS"
```
