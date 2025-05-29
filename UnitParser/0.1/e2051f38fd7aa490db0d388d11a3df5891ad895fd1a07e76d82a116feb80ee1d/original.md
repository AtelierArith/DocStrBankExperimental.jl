```
short_form(unit_name::AstractString)
```

Reduce the natural name of a units to its symbolic form for prefix and name.

If no match is found, return the original str.

# Example

julia> short_form("micrometers") ("μ", "m")

# Return

unit_prefix: String     Short form representing the prefix of the units, e.g. "k" for "kilo".     Set to empty str if the units had no prefix.

core_unit: String     Short form representing the units, e.g. "A" for "ampere".
