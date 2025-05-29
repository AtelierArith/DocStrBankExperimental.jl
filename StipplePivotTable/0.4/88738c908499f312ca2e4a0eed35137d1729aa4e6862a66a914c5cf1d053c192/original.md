```
Value
```

A mutable struct representing a value in a pivot table.

# Fields

  * `field::Union{String, Symbol}`: The field name associated with the value.
  * `aggregation::Union{String, Symbol}`: The aggregation method to be applied to the field.
  * `formula::Union{String, Symbol, Nothing}`: An optional formula for calculating the value. Defaults to `nothing`.
  * `label::Union{String, Symbol}`: A label for the value. Defaults to the value of `field`.
  * `format::Union{<:ValueFormatter, Nothing}`: An optional formatter for the value. Defaults to `nothing`.
