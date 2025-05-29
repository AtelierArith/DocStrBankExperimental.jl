```
matching_pokemon(name::AbstractString; tol=0.0, complete=false) → species
```

Return a list of `Species` objects that match the given name. If `complete` is `true`, the name must match exactly.

`tol` represents a tolerance on the Levenshtein distance between the name and the species name.

# Examples

```jldoctest
julia> matching_pokemon("rattata")
2-element Vector{Species}:
 RATTATA (NORMAL): (103, 70, 102); Fast: ["TACKLE_FAST", "QUICK_ATTACK_FAST"]; Charged: ["DIG", "HYPER_FANG", "BODY_SLAM"]
 RATTATA_ALOLA (DARK/NORMAL): (103, 70, 102); Fast: ["TACKLE_FAST", "QUICK_ATTACK_FAST"]; Charged: ["CRUNCH", "HYPER_FANG", "SHADOW_BALL"]

julia> matching_pokemon("rattata"; complete=true)
1-element Vector{Species}:
 RATTATA (NORMAL): (103, 70, 102); Fast: ["TACKLE_FAST", "QUICK_ATTACK_FAST"]; Charged: ["DIG", "HYPER_FANG", "BODY_SLAM"]

julia> matching_pokemon("rattatta")      # misspelled
Species[]

julia> matching_pokemon("rattatta"; tol=0.25)
2-element Vector{Species}:
 RATTATA (NORMAL): (103, 70, 102); Fast: ["TACKLE_FAST", "QUICK_ATTACK_FAST"]; Charged: ["DIG", "HYPER_FANG", "BODY_SLAM"]
 RATTATA_ALOLA (DARK/NORMAL): (103, 70, 102); Fast: ["TACKLE_FAST", "QUICK_ATTACK_FAST"]; Charged: ["CRUNCH", "HYPER_FANG", "SHADOW_BALL"]
```
