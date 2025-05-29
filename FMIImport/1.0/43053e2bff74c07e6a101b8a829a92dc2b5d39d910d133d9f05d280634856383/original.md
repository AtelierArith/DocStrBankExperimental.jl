```
fmi2EnterInitializationMode(c::FMU2Component)
```

Informs the FMU to enter Initialization Mode. Before calling this function, all variables with attribute <ScalarVariable initial = "exact" or "approx"> can be set with the “fmi2SetXXX” functions (the ScalarVariable attributes are defined in the Model Description File, see section 2.2.7). Setting other variables is not allowed. Furthermore, `fmi2SetupExperiment` must be called at least once before calling `fmi2EnterInitializationMode`, in order that `startTime` is defined.

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
