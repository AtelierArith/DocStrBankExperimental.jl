```
fmi3GetUInt16(c::FMU3Instance, vr::fmi3ValueReferenceFormat)
```

Get the values of an array of fmi3UInt16 variables.

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `vr::fmi3ValueReferenceFormat`: wildcards for how a user can pass a fmi[X]ValueReference

More detailed: `fmi3ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi3ValueReference, Array{fmi3ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

# Returns

  * `values::Array{fmi3UInt16}`: returns values of an array of fmi3UInt16 variables with the dimension of fmi3ValueReferenceFormat length.

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.4 Status Returned by Functions
  * FMISpec3.0: 2.2.6.2. Getting and Setting Variable Values

See also [`fmi3GetUInt16`](@ref).
