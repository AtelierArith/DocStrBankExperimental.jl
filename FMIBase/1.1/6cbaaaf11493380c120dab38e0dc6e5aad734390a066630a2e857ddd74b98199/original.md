```
getValue!(comp::FMU2Component, vrs::fmi2ValueReferenceFormat, dst::AbstractArray)
```

Retrieves values for the refernces `vrs` and stores them in `dst`

# Arguments

  * `comp::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `vrs::fmi2ValueReferenceFormat`: wildcards for how a user can pass a fmi[X]ValueReference
  * `dst::AbstractArray`: The array of destinations, must match the data types of the value references.

# Returns

  * `retcodes::Array{fmi2Status}`: Returns an array of length length(vrs) with Type `fmi2Status`. Type `fmi2Status` is an enumeration and indicates the success of the function call.
