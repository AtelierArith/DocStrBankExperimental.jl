```
fmi3GetVariableDependencies!(c::FMU3Instance, vr::fmi3ValueReference, elementIndiceOfDependents::AbstractArray{Csize_t}, independents::AbstractArray{fmi3ValueReference},  
    elementIndiceOfInpendents::AbstractArray{Csize_t}, dependencyKind::AbstractArray{fmi3DependencyKind}, ndependencies::Csize_t)
```

The actual dependencies (of type dependenciesKind) can be retrieved by calling the function fmi3GetVariableDependencies:

# Arguments

  * `c::FMU3Instance`: Argument `c` is a Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.
  * `vr::fmi3ValueReference`: Argument `vr` is the value handel called "ValueReference" that define the variable that shall be inquired.
  * `nvr::Csize_t`: Argument `nvr` defines the size of `vr`.
  * `elementIndiceOfDependents::AbstractArray{Csize_t}`: must point to a buffer of size_t values of size `nDependencies` allocated by the calling environment.    It is filled in by this function with the element index of the dependent variable that dependency information is provided for. The element indices start with 1. Using the element index 0 means all elements of the variable. (Note: If an array has more than one dimension the indices are serialized in the same order as defined for values in Section 2.2.6.1.)
  * `independents::AbstractArray{fmi3ValueReference}`:  must point to a buffer of `fmi3ValueReference` values of size `nDependencies` allocated by the calling environment.    It is filled in by this function with the value reference of the independent variable that this dependency entry is dependent upon.
  * `elementIndiceOfInpendents::AbstractArray{Csize_t}`: must point to a buffer of size_t `values` of size `nDependencies` allocated by the calling environment.    It is filled in by this function with the element index of the independent variable that this dependency entry is dependent upon. The element indices start with 1. Using the element index 0 means all elements of the variable. (Note: If an array has more than one dimension the indices are serialized in the same order as defined for values in Section 2.2.6.1.)
  * `dependencyKind::AbstractArray{fmi3DependencyKind}`: must point to a buffer of dependenciesKind values of size `nDependencies` allocated by the calling environment.    It is filled in by this function with the enumeration value describing the dependency of this dependency entry.
  * `ndependencies::Csize_t`: specifies the number of dependencies that the calling environment allocated space for in the result buffers, and should correspond to value obtained by calling `fmi3GetNumberOfVariableDependencies`.

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
  * FMISpec3.0: 2.2.10. Dependencies of Variables

See also [`fmi3GetVariableDependencies!`](@ref).
