```
Field::AbstractField(
    name::String
    args::Vector{Union{String,Number}}
    sortable::Bool
    no_index::Bool
    as_name::Union{String,Nothing}
)
```

Field object to include in RediSearch schema.

# Arguments

  * `name::String`: Name of the field.

# KeyWords

  * `args::Vector{Union{String,Number}}`: List of Arguments fot the field.
  * `sortable::Bool`: Sortable status.
  * `no_index::Bool`: Index Status.
  * `as_name::Union{String,Nothing}`: Name to reference field as.

# Returns

  * `Field::AbstractField`
