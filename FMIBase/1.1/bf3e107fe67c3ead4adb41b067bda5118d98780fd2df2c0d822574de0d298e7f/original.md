```
getValue(comp::FMU2Component, vrs::fmi2ValueReferenceFormat)
```

Returns the specific value of `fmi2ScalarVariable` containing the modelVariables with the identical fmi2ValueReference in an array.

# Arguments

  * `comp::FMU2Component`: Mutable struct represents an instantiated instance of an FMU in the FMI 2.0.2 Standard.
  * `vrs::fmi2ValueReferenceFormat`: wildcards for how a user can pass a fmi[X]ValueReference

More detailed: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

# Returns

  * `dstArray::Array{Any,1}(undef, length(vrs))`: Stores the specific value of `fmi2ScalarVariable` containing the modelVariables with the identical fmi2ValueReference to the input variable vr (vr = vrs[i]). `dstArray` is a 1-Dimensional Array that has the same length as `vrs`.
