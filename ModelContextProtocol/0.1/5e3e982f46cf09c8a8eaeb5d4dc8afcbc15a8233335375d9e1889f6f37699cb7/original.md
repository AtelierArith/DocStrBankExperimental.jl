```
ListToolsResult(; tools::Vector{Dict{String,Any}}, 
              nextCursor::Union{String,Nothing}=nothing) <: ResponseResult
```

Result returned from a list tools request.

# Fields

  * `tools::Vector{Dict{String,Any}}`: List of available tools with their metadata
  * `nextCursor::Union{String,Nothing}`: Optional pagination cursor for fetching more tools
