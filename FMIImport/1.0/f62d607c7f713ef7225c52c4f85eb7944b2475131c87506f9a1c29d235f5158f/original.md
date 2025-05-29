```
fmi3Reset(c::FMU3Instance; soft::Bool = false)
```

Is called by the environment to reset the FMU after a simulation run. The FMU goes into the same state as if `fmi3InstantiateXXX` would have been called.

# Arguments

  * `c::FMU3Instance`: Argument `c` is a Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.

# Keywords

  * `soft::Bool=false`: If the Keyword `soft = true` the `fmi3Teminate` needs to be called in state `fmi3InstanceStateContinuousTimeMode` or `fmi3InstanceStateEventMode`.

# Returns

  * `status::fmi3Status`: Return `status` is an enumeration of type `fmi3Status` and indicates the success of the function call.

More detailed:     - `fmi3OK`: all well     - `fmi3Warning`: things are not quite right, but the computation can continue     - `fmi3Discard`: if the slave computed successfully only a subinterval of the communication step     - `fmi3Error`: the communication step could not be carried out at all     - `fmi3Fatal`: if an error occurred which corrupted the FMU irreparably

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 2.2.4 Status Returned by Functions
  * FMISpec3.0: 2.3.1. Super State: FMU State Setable

See also [`fmi3Reset`](@ref).
