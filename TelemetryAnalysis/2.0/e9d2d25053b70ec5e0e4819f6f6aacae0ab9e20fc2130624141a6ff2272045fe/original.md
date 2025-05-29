```
struct TelemetryVariableDescription
```

Describe a variable in the telemetry database.

# Fields

  * `alias::Union{Nothing, Symbol}`: An alias of the variable.
  * `default_view::Symbol`: Select the default view for this variable during processing. For   the list of available options, see [`process_telemetries`](@ref).   (**Default** = `:processed`)
  * `dependencies::Union{Nothing, Vector{Symbol}}`: A vector containing a list of dependencies   required to obtain the processed value of this variable. If it is `nothing`, the   variable does not have dependencies.
  * `description::String`: A description about the variable.
  * `endianess::Symbol`: `:littleendian` or `:bigendian` to indicate the endianess of the   variable.
  * `label::Symbol`: Variable label.
  * `position::Int`: Variable position in the unpacked telemetry frame.
  * `size::Int`: Number of bytes of the variable.
  * `btf::Function`: Bit transfer function to obtain the variable byte array data from the   telemetry frame.
  * `rtf::Function`: Raw transfer function to obtain the raw value from the byte array.
  * `tf::Function`: Transfer function to obtain the processed value.
