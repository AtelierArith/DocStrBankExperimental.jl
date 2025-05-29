```
lineage_ids(poke::Pokemon) → ids
lineage_ids(species::Species) → ids
lineage_ids(list) → ids
```

`poke` または `species` のさらなる進化を ID のリストとして返します。

# 例

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
