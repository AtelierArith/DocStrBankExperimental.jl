```
fmi3GetContinuousStateDerivatives!(c::FMU3Instance,
                        derivatives::AbstractArray{fmi3Float64},
                        nx::Csize_t)
```

Compute state derivatives at the current time instant and for the current states.

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `derivatives::AbstractArray{fmi3Float64}`: Argument `derivatives` contains values of type `fmi3Float64` which is a alias type for `Real` data type.`derivatives` is the `AbstractArray` which contains the `Real` values of the vector that represent the derivatives. The ordering of the elements of the derivatives vector is identical to the ordering of the state vector.
  * `nx::Csize_t`: Argument `nx` defines the length of vector `derivatives` and is provided for checking purposes

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

See also [`fmi3GetContinuousStateDerivatives!`](@ref).
