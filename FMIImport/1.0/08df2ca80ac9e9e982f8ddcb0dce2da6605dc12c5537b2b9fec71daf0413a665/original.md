```
fmi2FreeFMUstate(c::FMU2Component, FMUstate::Ref{fmi2FMUstate})
```

Frees all memory and other resources allocated with the fmi2GetFMUstate call for this FMUstate.

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `FMUstate::Ref{fmi2FMUstate}`: Argument `FMUstate` is an object that safely references data of type `fmi3FMUstate` which is a pointer to a data structure in the FMU that saves the internal FMU state of the actual or a previous time instant.

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

See also [`fmi2FreeFMUstate`](@ref).
