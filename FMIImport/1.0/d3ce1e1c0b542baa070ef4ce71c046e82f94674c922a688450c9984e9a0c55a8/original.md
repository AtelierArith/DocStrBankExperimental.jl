```
fmi3CompletedIntegratorStep!(c::FMU3Instance,
                                  noSetFMUStatePriorToCurrentPoint::fmi3Boolean,
                                  enterEventMode::Ref{fmi3Boolean},
                                  terminateSimulation::Ref{fmi3Boolean})
```

This function must be called by the environment after every completed step of the integrator provided the capability flag `needsCompletedIntegratorStep == true`. If `enterEventMode == fmi3True`, the event mode must be entered If `terminateSimulation == fmi3True`, the simulation shall be terminated

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `noSetFMUStatePriorToCurrentPoint::fmi3Boolean`: Argument `noSetFMUStatePriorToCurrentPoint = fmi3True` if `fmi3SetFMUState`  will no longer be called for time instants prior to current time in this simulation run.
  * `enterEventMode::Ref{fmi3Boolean}`: Argument `enterEventMode` points to the return value (fmi3Boolean) which signals to the environment if the FMU shall call `fmi3EnterEventMode`. `fmi3Boolean` is an alias type for `Boolean` data type.
  * `terminateSimulation::Ref{fmi3Boolean}`: Argument `terminateSimulation` points to the return value (fmi3Boolean) which signals signal if the simulation shall be terminated. `fmi3Boolean` is an alias type for `Boolean` data type.

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
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 2.2.4 Status Returned by Functions
  * FMISpec3.0: 3.2.1. State: Continuous-Time Mode

See also [`fmi3CompletedIntegratorStep!`](@ref).
