```
only_pokemon(name::AbstractString; exact=false, equiv=false, kwargs...) → species
```

Return the `Species` object that matches the given name, and throw an error if more than one matches.

If `exact` is `true`, only exact matches of the name are considered. If `equiv` is `true`, an error is not thrown if all matches are equivalent in their types, base stats, and moves.

# Examples

```jldoctest
julia> only_pokemon("scatterbug")
ERROR: multiple matching pokemon were found: ["SCATTERBUG", "SCATTERBUG_ARCHIPELAGO", "SCATTERBUG_CONTINENTAL", "SCATTERBUG_ELEGANT", "SCATTERBUG_FANCY", "SCATTERBUG_GARDEN", "SCATTERBUG_HIGH_PLAINS", "SCATTERBUG_ICY_SNOW", "SCATTERBUG_JUNGLE", "SCATTERBUG_MARINE", "SCATTERBUG_MEADOW", "SCATTERBUG_MODERN", "SCATTERBUG_MONSOON", "SCATTERBUG_OCEAN", "SCATTERBUG_POKEBALL", "SCATTERBUG_POLAR", "SCATTERBUG_RIVER", "SCATTERBUG_SANDSTORM", "SCATTERBUG_SAVANNA", "SCATTERBUG_SUN", "SCATTERBUG_TUNDRA"]

julia> only_pokemon("scatterbug"; equiv=true)
SCATTERBUG (BUG): (63, 63, 116); Fast: ["BUG_BITE_FAST", "TACKLE_FAST"]; Charged: ["STRUGGLE"]
```
