```
fmi2GetIntegerStatus!(c::FMU2Component, 
                            s::fmi2StatusKind, 
                            value::Ref{fmi2Integer})
```

Informs the master about the actual status of the simulation run. Which status information is to be returned is specified by the argument `fmi2StatusKind`.

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `s::fmi2StatusKind`: Argument `s` defines which status information is to be returned. `fmi2StatusKind` is an enumeration that defines which status is inquired.

The following status information can be retrieved from a slave:

  * `fmi2DoStepStatus::fmi2Status`: Can be called when the `fmi2DoStep` function returned `fmi2Pending`. The function delivers `fmi2Pending` if the computation is not finished. Otherwise the function returns the result of the asynchronously executed `fmi2DoStep` call.
  * `fmi2PendingStatus::fmi2String`: Can be called when the `fmi2DoStep` function returned `fmi2Pending`. The function delivers a string which informs about the status of the currently running asynchronous `fmi2DoStep` computation
  * `fmi2LastSuccessfulTime:: fmi2Real`: Returns the end time of the last successfully completed communication step. Can be called after fmi2DoStep(..) returned fmi2Discard.
  * `fmi2Terminated::fmi2Boolean`: Returns `fmi2True`, if the slave wants to terminate the simulation. Can be called after fmi2DoStep(..) returned `fmi2Discard`. Use fmi2LastSuccessfulTime to determine the time instant at which the slave terminated.
  * `value::Ref{fmi2Integer}`: Argument `value` points to the return value (fmi2Integer) which was requested. `fmi2Integer` is a alias type for `Integer` data type.

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
  * FMISpec2.0.2[p.106]: 4.2.3 Retrieving Status Information from the Slave

See also [`fmi2GetIntegerStatus!`](@ref).
