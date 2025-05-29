```
get_table(data::T) where T<:WiNDCtable
```

Return the main table of the WiNDCtable object as a DataFrame

## Required Arguments

1. `data` - A WiNDCtable-like object.

## Output

Returns a DataFrame with columns `domain(data)`, `subtable`, and `value`.
