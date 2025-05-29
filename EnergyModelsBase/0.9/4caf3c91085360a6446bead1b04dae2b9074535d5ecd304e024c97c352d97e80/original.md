```
struct EmissionsProcess{T} <: EmissionsData{T}

EmissionsProcess(emissions::Dict{<:ResourceEmit,T}) where T
EmissionsProcess(emissions::Dict{<:ResourceEmit,T}, _) where T
EmissionsProcess()
```

No capture, but process emissions are present. Does not require `co2_capture` as input, but accepts it and will ignore it, if provided.

# Fields

  * **`emissions::Dict{ResourceEmit, T}`**: emissions per unit produced.
