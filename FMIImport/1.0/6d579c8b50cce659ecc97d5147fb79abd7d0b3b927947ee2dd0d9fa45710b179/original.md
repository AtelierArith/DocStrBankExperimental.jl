```
fmi3FreeInstance!(c::FMU3Instance; popInstance::Bool = true)
```

Disposes the given instance, unloads the loaded model, and frees all the allocated memory and other resources that have been allocated by the functions of the FMU interface. If a null pointer is provided for “c”, the function call is ignored (does not have an effect).

Removes the component from the FMUs component list.

# Arguments

  * `c::FMU3Instance`: Argument `c` is a Mutable struct represents an instantiated instance of an FMU in the FMI 3.0 Standard.

# Keywords

  * `popInstance::Bool=true`: If the Keyword `popInstance = true` the freed instance is deleted

# Returns

  * nothing

# Source

  * FMISpec3.0 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0, Version D5ef1c1: 2.3.1. Super State: FMU State Setable
