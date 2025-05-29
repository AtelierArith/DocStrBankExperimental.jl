```
fmi3GetNumberOfContinuousStates(c::FMU3Instance)
```

This function returns the number of continuous states. This function can only be called in Model Exchange. 

`fmi3GetNumberOfContinuousStates` must be called after a structural parameter is changed. As long as no structural parameters changed, the number of states is given in the modelDescription.xml, alleviating the need to call this function.

# Arguments

  * `c::FMU3Instance`: Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.

# Returns

  * `size::Integer`: Return `size` is the number of continuous states of this instance

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0: 2.2.3 Platform Dependent Definitions
  * FMISpec3.0: 2.3.2. State: Instantiated

See also [`fmi3GetNumberOfContinuousStates`](@ref).
