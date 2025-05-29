```
Filter
```

A mutable struct representing a filter with various attributes.

# Fields

  * `field::Union{String, Symbol}`: The field to which the filter is applied.
  * `condition::Union{String, Symbol}`: The condition to be applied on the field.
  * `type::Union{String, Symbol, Nothing}`: The type of the filter, default is `nothing`.
  * `value::Union{Any, Nothing}`: The value for the filter, default is `nothing`.
  * `selected_values::Union{Any, Vector, Nothing}`: The selected values for the filter, default is `nothing`.

# Constructor

  * `Filter(field::Union{String, Symbol}; kwargs...)`: Create a `Filter` instance with the specified field and keyword arguments for other attributes.
