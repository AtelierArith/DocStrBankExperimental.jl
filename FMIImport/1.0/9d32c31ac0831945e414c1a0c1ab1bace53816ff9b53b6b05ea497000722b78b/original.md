```
fmi2SetFMUstate(c::FMU2Component, FMUstate::fmi2FMUstate)
```

Copies the content of the previously copied FMUstate back and uses it as actual new FMU state.

# Arguments

  * `str::fmi2Struct`:  Representative for an FMU in the FMI 2.0.2 Standard.

More detailed: `fmi2Struct = Union{FMU2, FMU2Component}`

  * `str::FMU2`: Mutable struct representing a FMU and all it instantiated instances in the FMI 2.0.2 Standard.
  * `str::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `FMUstate::fmi2FMUstate`: Argument `FMUstate` is a pointer to a data structure in the FMU that saves the internal FMU state of the actual or a previous time instant.

# Returns

  * `status::fmi2Status`: Return `status` is an enumeration of type `fmi2Status` and indicates the success of the function call.

More detailed:

  * `fmi2OK`: all well
  * `fmi2Warning`: things are not quite right, but the computation can continue
  * `fmi2Discard`: if the slave computed successfully only a subinterval of the communication step
  * `fmi2Error`: the communication step could not be carried out at all
  * `fmi2Fatal`: if an error occurred which corrupted the FMU irreparably
  * `fmi2Pending`: this status is returned if the slave executes the function asynchronously

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.25]: 2.1.8 Getting and Setting the Complete FMU State

See also [`fmi2GetFMUstate`](@ref).
