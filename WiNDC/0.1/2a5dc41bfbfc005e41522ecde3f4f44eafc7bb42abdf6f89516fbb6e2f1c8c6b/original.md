```
get_set(data::T) where T<:WiNDCtable  

get_set(data::T, set_name::String) where T<:WiNDCtable

get_set(data::T, set_name::Vector{String}) where T<:WiNDCtable
```

Return the elements of the given sets. If no set is given, return all sets.

## Required Arguments

1. `data` - A WiNDCtable-like object.
2. `set_name` - A string or vector of strings representing the set names to be extracted.

## Returns

Returns a DataFrame with three columns, `:element`, `:set` and `:description`
