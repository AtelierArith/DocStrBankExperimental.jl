```
fmi3SetClock(c::FMU3Instance, vr::fmi3ValueReferenceFormat, valueSizes::Union{AbstractArray{Csize_t}, Csize_t}, values::Union{AbstractArray{fmi3Clock}, fmi3Clock})
```

Set the values of an array of clock variables

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `vr::fmi3ValueReferenceFormat`: Wildcards for how a user can pass a fmi[X]ValueReference

More detailed: `fmi3ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi3ValueReference, Array{fmi3ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

  * `values::Union{AbstractArray{fmi3Clock}, fmi3Clock}`: Argument `values` is an AbstractArray with the actual values of these variables.

# Returns

  * `status::fmi3Status`: Return `status` is an enumeration of type `fmi3Status` and indicates the success of the function call.

More detailed:

  * `fmi3OK`: all well
  * `fmi3Warning`: things are not quite right, but the computation can continue
  * `fmi3Discard`: if the slave computed successfully only a subinterval of the communication step
  * `fmi3Error`: the communication step could not be carried out at all
  * `fmi3Fatal`: if an error occurred which corrupted the FMU irreparably

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.4 Status Returned by Functions
  * FMISpec3.0: 2.2.6.2. Getting and Setting Variable Values

See also [`fmi3SetClock`](@ref).
