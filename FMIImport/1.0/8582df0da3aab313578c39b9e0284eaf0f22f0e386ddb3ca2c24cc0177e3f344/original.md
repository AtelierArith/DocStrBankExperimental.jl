```
fmi3SetContinuousStates(c::FMU3Instance,
    x::AbstractArray{fmi3Float64},
    nx::Csize_t)
```

Set a new (continuous) state vector and re-initialize caching of variables that depend on the states. Argument nx is the length of vector x and is provided for checking purposes

If `fmi3UpdateDiscreteStates` returned with `nominalsOfContinuousStatesChanged == fmi3True`, then at least one nominal value of the states has changed and can be inquired with `fmi3GetNominalsOfContinuousStates`. Not allowed in Co-Simulation and Scheduled Execution.

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `x::AbstractArray{fmi3Float64}`: Argument `x` contains values of type `fmi3Float64` which is a alias type for `Real` data type. `x` is the `AbstractArray` which contains the `Real` values of the vector that represent the nominal values of the continuous states.
  * `nx::Csize_t`: Argument `nx` defines the length of vector `x` and is provided for checking purposes

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

See also [`fmi3SetContinuousStates`](@ref).
