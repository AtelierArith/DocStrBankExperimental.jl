```julia
StructField(
;
    name,
    data_type,
    default,
    comment,
    needs_conversion,
    exclude_setter,
    valid_range,
    validation_action,
    null_value,
    internal_default
)

```

Construct a StructField for code auto-generation purposes.

# Arguments

  * `name::String`: Field name
  * `data_type::Union{DataType, String}`: Field type
  * `default::Any`: The generated constructors will define this as a default value.
  * `comment::String`: Include this comment above the field name. Defaults to empty string.
  * `needs_conversion::Bool`: Set to true if the getter and setter functions need to apply unit conversion. The type must implement `get_value(::Component, ::Type)` and `set_value(::Component, ::Type)` for this combination of component type and field type.
  * `exclude_setter::Bool`: Do not generate a setter function for this field. Defaults to false.
  * `valid_range::Union{Nothing, String, Dict}`: Enables range validation when the component is added to a system. Define this as a Dict with "min" and "max" or as a String with the field name in the struct that defines this field's valid range and InfrastructureSystems will validate any value against that range. Use `nothing` if one doesn't apply, such as if there is no max limit.
  * `validation_action`: Define this as "error" or "warn". If it is "error" then InfrastructureSystems will throw an exception if the validation code detects a problem. Otherwise, it will log a warning.
  * `null_value::Any`: Value to indicate the field is zero or empty, such as 0.0 for Float64. If all members in the struct define this field then a "demo" constructor will be generated. This allows entering `val = MyType(nothing)` in the REPL to see the layout of a struct without worrying about valid values.
  * `internal_default`: Set to true for non-user-facing fields like `InfrastructureSystemsInternal` that have default values.
