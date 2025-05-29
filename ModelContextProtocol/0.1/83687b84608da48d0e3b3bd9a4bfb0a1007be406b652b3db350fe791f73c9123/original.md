```
ListPromptsResult(; prompts::Vector{Dict{String,Any}}, 
                nextCursor::Union{String,Nothing}=nothing) <: ResponseResult
```

Result returned from a list prompts request.

# Fields

  * `prompts::Vector{Dict{String,Any}}`: List of available prompts with their metadata
  * `nextCursor::Union{String,Nothing}`: Optional pagination cursor for fetching more prompts
