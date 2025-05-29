```
Pokemon(id, level, ivs; name=display_name(id), islucky=false, mutation='N', isshiny=false, mega=false, max='N', maxlevel=nothing, raid_tier=nothing, max_tier=nothing)
Pokemon(id, ivs; cp, kwargs...)
```

Construct a Pokemon. `id` is either a `Species` or a valid argument for `only_pokemon(id; exact=true)`. If `level` is not supplied, `cp` is an obligate keyword argument. `mega` is typically `true` or `false`, except in cases (like Charizard) where one should supply a `Char` to disambiguate the mega (e.g., `'X'` or `'Y'`).

# Examples

```julia
julia> Pokemon("Ralts", (8, 12, 10); cp=204)
Ralts; CP: 204; level: 15.0; IVs: (8, 12, 10)

julia> Pokemon("LUCARIO", 20.0, (15, 12, 13); name="Wiley")
Wiley (Lucario); CP: 1521; level: 20.0; IVs: (15, 12, 13)
```
