```
fmi3EnterContinuousTimeMode(c::FMU3Instance; soft::Bool=false)
```

The model enters Continuous-Time Mode and all discrete-time equations become inactive and all relations are “frozen”. This function has to be called when changing from Event Mode (after the global event iteration in Event Mode over all involved FMUs and other models has converged) into Continuous-Time Mode.

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.

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
  * FMISpec3.0: 2.3.5. State: Event Mode

See also [`fmi3EnterContinuousTimeMode`](@ref).
