```julia
function sameParams(𝐒        :: FDobjectsVector,
                    funcname :: String)
```

Return true if all objects in 𝐒 have the same `sr`, `wl`, `DC`, `taper`, `func`(only for [SpectraVector](@ref) objects), `nonlinear` (only for [CrossSpectraVector](@ref) and [CoherenceVector](@ref)) and `smoothing` fields, otherwise print an error message pointing to the first field that is not identical in all objects and return `Nothing`. This method applies to all [FDobjectsVector](@ref) types, that is, to [SpectraVector](@ref), [CrossSpectraVector](@ref) and [CoherenceVector](@ref).

`funcname` is an optional string that the user can provide. It is inserted into the error message to locate the part of the code that generated the error. By defalut, "unknown" is used.
