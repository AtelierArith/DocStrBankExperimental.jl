```
get_subtable(data::T, subtable::String, column::Vector{Symbol}; negative::Bool = false, keep_all_columns = false) where T<:WiNDCtable

get_subtable(data::T, subtable::String; column::Symbol = :value, output::Symbol = :value, negative = false) where T<:WiNDCtable

get_subtable(data::T, subtable::Vector{String}) where T<:WiNDCtable
```

Return the subtables requested as a DataFrame

## Required Arguments

1. `data` - A WiNDCtable-like object.
2. `subtable` - A string or vector of strings representing the subtable names to be extracted.

## Optional Arguments

  * `column` - A symbol representing the column to be extracted. Default is `:value`.
  * `output` - A symbol representing the output column name. Default is `:value`.
  * `negative` - A boolean representing whether the values should be negated. Default is `false`.

## Returns

Returns a DataFrame with the requested subtables and columns.
