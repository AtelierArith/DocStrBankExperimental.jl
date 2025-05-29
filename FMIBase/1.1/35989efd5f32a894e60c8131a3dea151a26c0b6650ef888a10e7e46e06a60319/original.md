```
getState(solution::FMUSolution, vr::fmi2ValueReferenceFormat; isIndex::Bool=false)
```

Returns the solution state.

# Arguments

  * `solution::FMUSolution`: Struct contains information about the solution `value`, `success`, `state` and  `events` of a specific FMU.
  * `vr::fmi2ValueReferenceFormat`: wildcards for how a user can pass a fmi[X]ValueReference (default = md.valueReferences)

More detailed: `fmi2ValueReferenceFormat = Union{Nothing, String, Array{String,1}, fmi2ValueReference, Array{fmi2ValueReference,1}, Int64, Array{Int64,1}, Symbol}`

  * `isIndex::Bool=false`: Argument `isIndex` exists to check if `vr` ist the specific solution element ("index") that equals the given fmi2ValueReferenceFormat

# Return

  * If he length of the given references equals 1, each element u in the collection `solution.states.u`, it is selecting the element at the index represented by indices[1] and returns it.

Thus, the collect() function is taking the generator expression and returning an array of the selected elements. 

  * If more than one reference is given, the same process takes place as before. The difference is that now more than one index is accessed.

# Source

  * FMISpec2.0.2 Link: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec2.0.2[p.22]: 2.1.2 Platform Dependent Definitions (fmi2TypesPlatform.h)
