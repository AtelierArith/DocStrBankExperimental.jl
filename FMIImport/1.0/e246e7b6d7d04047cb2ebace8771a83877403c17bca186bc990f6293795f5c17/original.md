```
fmi3ActivateModelPartition(c::FMU3Instance, vr::fmi3ValueReference, activationTime::AbstractArray{fmi3Float64})
```

During Clock Activation Mode (see 5.2.2.) after `fmi3ActivateModelPartition` has been called for a calculated, tunable or changing Clock the FMU provides the information on when the Clock will tick again, i.e. when the corresponding model partition has to be scheduled the next time.

Each `fmi3ActivateModelPartition` call is associated with the computation of an exposed model partition of the FMU and therefore to an input Clock.

# TODO argmuents

# Arguments

  * `c::FMU3Instance`: Argument `c` is a Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `vr::fmi3ValueReference`: Argument `vr` is the value handel called "ValueReference" that define the variable that shall be inquired.
  * `activationTime::AbstractArray{fmi3Float64}`:

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
  * FMISpec3.0: 5.2.2. State: Clock Activation Mode

See also [`fmi3ActivateModelPartition`](@ref).
