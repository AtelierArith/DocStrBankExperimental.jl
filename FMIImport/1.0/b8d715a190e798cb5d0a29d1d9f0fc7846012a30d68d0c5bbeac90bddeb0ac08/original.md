```
fmi3GetNumberOfVariableDependencies(c::FMU3Instance, vr::fmi3ValueReference, nvr::Ref{Csize_t})
```

The number of dependencies of a given variable, which may change if structural parameters are changed, can be retrieved by calling fmi3GetNumberOfVariableDependencies.

This information can only be retrieved if the 'providesPerElementDependencies' tag in the ModelDescription is set.

# Arguments

  * `c::FMU3Instance`: Argument `c` is a Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `vr::Union{fmi3ValueReference, String}`: Argument `vr` is the value handel called "ValueReference" that define the variable that shall be inquired.

# Returns

  * `size::Integer`: Return `size` is the number of variable dependencies for the given variable

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 2.2.10. Dependencies of Variables

See also [`fmi3GetNumberOfVariableDependencies`](@ref).
