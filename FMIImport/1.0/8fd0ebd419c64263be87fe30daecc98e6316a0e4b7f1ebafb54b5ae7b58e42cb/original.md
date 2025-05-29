```
fmi3GetOutputDerivatives!(c::FMU3Instance, vr::AbstractArray{fmi3ValueReference}, nValueReferences::Csize_t, order::AbstractArray{fmi3Int32}, values::AbstractArray{fmi3Float64}, nValues::Csize_t)
```

Retrieves the n-th derivative of output values.

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `vr::Array{fmi3ValueReference}`: Argument `vr` is an array of `nValueReferences` value handels called "ValueReference" that t define the variables whose derivatives shall be set.
  * `nValueReferences::Csize_t`: Argument `nValueReferences` defines the size of `vr`.
  * `order::Array{fmi3Int32}`: Argument `order` is an array of fmi3Int32 values witch specifys the corresponding order of derivative of the real input variable.
  * `values::Array{fmi3Float64}`: Argument `values` is an array with the actual values of these variables.
  * `nValues::Csize_t`: Argument `nValues` defines the size of `values`.

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
  * FMISpec3.0: 2.2.12. Getting Derivatives of Continuous Outputs

See also [`fmi3GetOutputDerivatives!`](@ref).
