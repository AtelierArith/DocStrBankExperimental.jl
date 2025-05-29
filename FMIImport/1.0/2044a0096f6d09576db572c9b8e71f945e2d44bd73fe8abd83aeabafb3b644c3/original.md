```
fmi3EnterEventMode(c::FMU3Instance, stepEvent::fmi3Boolean, stateEvent::fmi3Boolean, rootsFound::AbstractArray{fmi3Int32}, nEventIndicators::Csize_t, timeEvent::fmi3Boolean; soft::Bool=false)
```

The model enters Event Mode from the Continuous-Time Mode in ModelExchange oder Step Mode in CoSimulation and discrete-time equations may become active (and relations are not “frozen”).

# TODO argmuents

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `stepEvent::fmi3Boolean`:
  * `stateEvent::fmi3Boolean`:
  * `rootsFound::AbstractArray{fmi3Int32}`:
  * `nEventIndicators::Csize_t`:
  * `timeEvent::fmi3Boolean`:
  * `soft::Bool=false`:

# Keywords

  * `soft::Bool=false`: If the Keyword `soft = true` the `fmi3Teminate` needs to be called in state  `fmi3InstanceStateContinuousTimeMode` or `fmi3InstanceStateEventMode`.

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

See also [`fmi3EnterEventMode`](@ref).
