```
fmi3GetContinuousStates!(c::FMU3Instance, nominals::AbstractArray{fmi3Float64}, nContinuousStates::Csize_t)
```

Return the states at the current time instant.

This function must be called if `fmi3UpdateDiscreteStates` returned with `valuesOfContinuousStatesChanged == fmi3True`. Not allowed in Co-Simulation and Scheduled Execution.

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `nominals::AbstractArray{fmi3Float64}`: Argument `nominals` contains values of type `fmi3Float64` which is a alias type for `Real` data type. `nominals` is the `AbstractArray` which contains the `Real` values of the vector that represent the new state vector.
  * `nContinuousStates::Csize_t`: Argument `nContinuousStates` defines the length of vector `nominals` and is provided for checking purposes

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
  * FMISpec3.0: 2.3.3. State: Initialization Mode

See also [`fmi3GetContinuousStates!`](@ref).
