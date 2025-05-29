```
fmi2ExitInitializationMode(c::FMU2Component)
```

Informs the FMU to exit Initialization Mode.

# Arguments

  * `c::FMU2Component`: Argument `c` is a Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.

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
  * FMISpec2.0.2[p.22]: 2.1.2 Platform Dependent Definitions (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.22]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.22]: 2.1.6 Initialization, Termination, and Resetting an FMU

See also [`fmi2EnterInitializationMode`](@ref).
