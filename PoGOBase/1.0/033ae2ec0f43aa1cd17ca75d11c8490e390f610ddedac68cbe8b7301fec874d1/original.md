```
matching_pokemon(name::AbstractString, types::AbstractString; kwargs...) → species
```

Return a list of `Species` objects that match the given name and types.

# Examples

```jldoctest
julia> matching_pokemon("rattata", "dark/normal")
1-element Vector{Species}:
 RATTATA_ALOLA (DARK/NORMAL): (103, 70, 102); Fast: ["TACKLE_FAST", "QUICK_ATTACK_FAST"]; Charged: ["CRUNCH", "HYPER_FANG", "SHADOW_BALL"]
```
