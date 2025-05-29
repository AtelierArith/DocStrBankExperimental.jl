```
fmi2GetFMUstate!(c::FMU2Component, FMUstate::Ref{fmi2FMUstate})
```

Makes a copy of the internal FMU state and returns a pointer to this copy.

# Arguments

  * `str::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `FMUstate::Ref{fmi2FMUstate}`:If on entry `FMUstate == NULL`, a new allocation is required. If `FMUstate != NULL`, then `FMUstate` points to a previously returned `FMUstate` that has not been modified since.

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
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions
  * FMISpec2.0.2[p.18]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.24]: 2.1.7 Getting and Setting Variable Values

See also [`fmi2GetFMUstate!`](@ref).
