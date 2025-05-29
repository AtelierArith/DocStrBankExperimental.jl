```julia
function sameParams(𝒀        :: TFobjectsVector,
                    funcname :: String) =
```

Return true if all objects in 𝒀 have the same `bandwidth`, `nonlinear`, `fsmoothing` and `tsmoothing` field, otherwise print an error message pointing to the first field that is not identical in all objects and return `Nothing`. This method applies to all [TFobjectsVector](@ref) types, that is, [TFAnalyticSignalVector](@ref), [TFAmplitudeVector](@ref) and [TFPhaseVector](@ref).

`funcname` has the same meaning as in the previous method.
