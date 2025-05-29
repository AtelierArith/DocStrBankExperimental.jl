```julia
getVariableType(_)

```

Variable nodes `variableType` information holding a variety of meta data associated with the type of variable stored in that node of the factor graph.

Notes

  * API Quirk in that this function returns and instance of `::T` not a `::Type{<:InferenceVariable}`.

DevWork

  * TODO, see IncrementalInference.jl 1228

Related

getVariableType
