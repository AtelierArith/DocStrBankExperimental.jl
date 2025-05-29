```
fmi2GetRealOutputDerivatives!(c::FMU2Component,  
                                vr::AbstractArray{fmi2ValueReference}, 
                                nvr::Csize_t, order::AbstractArray{fmi2Integer}, 
                                value::AbstractArray{fmi2Real})
```

Sets the n-th time derivative of real input variables.

# Arguments

  * `c::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `vr::Array{fmi2ValueReference}`: Argument `vr` is an array of `nvr` value handels called "ValueReference" that t define the variables whose derivatives shall be set.
  * `nvr::Csize_t`: Argument `nvr` defines the size of `vr`.
  * `order::Array{fmi2Integer}`: Argument `order` is an array of fmi2Integer values witch specifys the corresponding order of derivative of the real input variable.
  * `values::Array{fmi2Real}`: Argument `values` is an array with the actual values of these variables.

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
  * FMISpec2.0.2[p.16]: 2.1.2 Platform Dependent Definitions
  * FMISpec2.0.2[p.18]: 2.1.3 Status Returned by Functions
  * FMISpec2.0.2[p.104]: 4.2.1 Transfer of Input / Output Values and Parameters
