```
ListResourcesResult(; resources::Vector{Dict{String,Any}}, 
                  nextCursor::Union{String,Nothing}=nothing) <: ResponseResult
```

Result returned from a list resources request.

# Fields

  * `resources::Vector{Dict{String,Any}}`: List of available resources with their metadata
  * `nextCursor::Union{String,Nothing}`: Optional pagination cursor for fetching more resources
