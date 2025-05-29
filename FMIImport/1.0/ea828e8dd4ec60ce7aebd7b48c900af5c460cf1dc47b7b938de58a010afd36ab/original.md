```
fmi3DoStep!(c::FMU3Instance, currentCommunicationPoint::Union{Real, Nothing} = nothing, communicationStepSize::Union{Real, Nothing} = nothing, noSetFMUStatePriorToCurrentPoint::Bool = true,
    eventEncountered::fmi3Boolean = fmi3False, terminateSimulation::fmi3Boolean = fmi3False, earlyReturn::fmi3Boolean = fmi3False, lastSuccessfulTime::fmi3Float64 = 0.0)
```

The computation of a time step is started.

# TODO argmuents

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `currentCommunicationPoint::Union{Real, Nothing} = nothing`
  * `communicationStepSize::Union{Real, Nothing} = nothing`
  * `noSetFMUStatePriorToCurrentPoint::Bool = true`
  * `eventEncountered::fmi3Boolean = fmi3False`
  * `terminateSimulation::fmi3Boolean = fmi3False`
  * `earlyReturn::fmi3Boolean = fmi3False`
  * `lastSuccessfulTime::fmi3Float64 = 0.0`

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
  * FMISpec3.0: 4.2.1. State: Step Mode

See also [`fmi3DoStep!`](@ref).
