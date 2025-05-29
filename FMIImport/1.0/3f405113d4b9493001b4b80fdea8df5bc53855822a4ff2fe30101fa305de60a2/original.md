```
fmi2GetDerivatives!(c::FMU2Component,
                   derivatives::AbstractArray{fmi2Real},
                   nx::Csize_t)
```

Compute state derivatives at the current time instant and for the current states.

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `derivatives::AbstractArray{fmi2Real}`: Argument `derivatives` contains values of type `fmi2Real` which is a alias type for `Real` data type.`derivatives` is the `AbstractArray` which contains the `Real` values of the vector that represent the derivatives. The ordering of the elements of the derivatives vector is identical to the ordering of the state vector.
  * `nx::Csize_t`: Argument `nx` defines the length of vector `derivatives` and is provided for checking purposes

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
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions (fmi2TypesPlatform.h)
  * FMISpec2.0.2[p.16]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.83]: 3.2.2 Evaluation of Model Equations

See also [`fmi2GetDerivatives!`](@ref).
