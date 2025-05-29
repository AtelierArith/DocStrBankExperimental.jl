```
setValue(component,
            vrs::fmi2ValueReferenceFormat,
            srcArray::AbstractArray;
            filter=nothing)
```

Stores the specific value of `fmi2ScalarVariable` containing the modelVariables with the identical fmi2ValueReference and returns an array that indicates the Status.

# Arguments

  * `comp::FMUInstance` (FMU2Component or FMU3Instance): Mutable struct represents an instantiated instance of an FMU in the FMI 2 or 3.
  * `vrs::fmi2ValueReferenceFormat`: wildcards for how a user can pass a fmi[X]ValueReference
  * `srcArray::AbstractArray`: Stores the specific value of `fmi2ScalarVariable` containing the modelVariables with the identical fmi2ValueReference to the input variable vr (vr = vrs[i]). `srcArray` has the same length as `vrs`.

# Keywords

  * `filter=nothing`: It is applied to each ModelVariable to determine if it should be updated.

# Returns

  * `retcodes::Array{fmi2Status}`: Returns an array of length length(vrs) with Type `fmi2Status`. Type `fmi2Status` is an enumeration and indicates the success of the function call.
