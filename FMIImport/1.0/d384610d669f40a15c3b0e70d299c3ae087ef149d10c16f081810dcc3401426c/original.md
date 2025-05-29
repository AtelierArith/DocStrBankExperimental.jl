```
fmi2SerializedFMUstateSize!(c::FMU2Component, FMUstate::fmi2FMUstate, size::Ref{Csize_t})
```

Stores the size of the byte vector in the given referenced Address, in order that FMUstate can be stored in it.

# Argument

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `FMUstate::fmi2FMUstate`: Argument `FMUstate` is a pointer to a data structure in the FMU that saves the internal FMU state of the actual or a previous time instant.
  * `size::Ref{Csize_t}`: Argument `size` is an object that safely references a value of type `Csize_t` and defines the size of the byte vector in which the FMUstate can be stored.

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

See also [`fmi2SerializedFMUstateSize!`](@ref).
