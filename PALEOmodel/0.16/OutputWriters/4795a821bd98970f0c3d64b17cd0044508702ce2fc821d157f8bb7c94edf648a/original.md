```
AbstractOutputWriter
```

Interface implemented by containers for PALEO model output.

Implementations should define methods for:

# Writing output

  * [`initialize!`](@ref)
  * [`add_record!`](@ref)

# Modifying output

  * [`PB.add_field!`](@ref)

# Querying output

  * [`PB.get_table`](@ref)
  * [`PB.show_variables`](@ref)
  * [`PB.has_variable`](@ref)

# Accessing output data

  * [`PALEOmodel.get_array`](@ref)
  * [`PB.get_field`](@ref)
  * [`PB.get_mesh`](@ref)
  * [`PB.get_data`](@ref)
