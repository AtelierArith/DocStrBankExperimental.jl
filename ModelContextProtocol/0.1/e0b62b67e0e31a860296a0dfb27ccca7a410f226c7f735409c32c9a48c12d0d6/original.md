```
ClientCapabilities(; experimental::Union{Dict{String,Dict{String,Any}},Nothing}=nothing,
                roots::Union{Dict{String,Bool},Nothing}=nothing,
                sampling::Union{Dict{String,Any},Nothing}=nothing)
```

Capabilities reported by an MCP client during initialization.

# Fields

  * `experimental::Union{Dict{String,Dict{String,Any}},Nothing}`: Experimental features supported
  * `roots::Union{Dict{String,Bool},Nothing}`: Root directories client has access to
  * `sampling::Union{Dict{String,Any},Nothing}`: Sampling capabilities for model generation
