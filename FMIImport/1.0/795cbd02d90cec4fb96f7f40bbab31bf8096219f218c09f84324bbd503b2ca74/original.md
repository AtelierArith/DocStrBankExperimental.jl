fmi3GetOutputDerivatives!(c::FMU3Instance, vr::AbstractArray{fmi3ValueReference}, nValueReferences::Csize*t, order::AbstractArray{fmi3Int32}, values::AbstractArray{fmi3Float64}, nValues::Csize*t)

Retrieves the n-th derivative of output values.

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `vr::Array{fmi3ValueReference}`: Argument `vr` is an array of `nValueReferences` value handels called "ValueReference" that t define the variables whose derivatives shall be set.
  * `order::Array{fmi3Int32}`: Argument `order` is an array of fmi3Int32 values witch specifys the corresponding order of derivative of the real input variable.

# Returns

  * `value::AbstactArray{fmi3Float64}`: Return `value` is an array which represents a vector with the values of the derivatives.

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 2.2.12. Getting Derivatives of Continuous Outputs

See also [`fmi3GetOutputDerivatives`](@ref).
