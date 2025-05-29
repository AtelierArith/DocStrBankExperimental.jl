```julia
StructDefinition(
;
    struct_name,
    fields,
    supertype,
    docstring,
    is_component
)

```

Construct a StructDefinition for code auto-generation purposes.

# Arguments

  * `struct_name::AbstractString`: Struct name
  * `fields::Vector{StructField}`: Struct fields. Refer to [`StructField`](@ref).
  * `docstring::AbstractString`: Struct docstring. Defaults to an empty string.
  * `supertype::Union{String, DataType}`: Struct supertype. Defaults to no supertype.
  * `is_component::Bool`: Set to true for component types that will be attached to a system. Do not set to Default to true.
