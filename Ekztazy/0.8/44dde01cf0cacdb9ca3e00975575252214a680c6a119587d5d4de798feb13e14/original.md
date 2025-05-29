```
split_message(text::AbstractString; chunk_limit::UInt=2000,
              extrastyles::Vector{Regex}=Vector{Regex}(),
              forcesplit::Bool = true) -> Vector{String}
```

Split a message into chunks with at most chunk_limit length, preserving formatting.

The `chunk_limit` has as default the 2000 character limit of Discord's messages, but can be changed to any nonnegative integer.

Formatting is specified by [`STYLES`](@ref)) and can be aggregated with the `extrastyles` argument.

Discord limits messages to 2000, so the code forces split if format breaking cannot be avoided. If desired, however, this behavior can be lifter by setting `forcesplit` to false.

## Examples

```julia
julia> split_message("foo")
1-element Vector{String}:
 "foo"

julia> split_message(repeat('.', 1995) * "**hello, world**")[2]
"**hello, world**"

julia> split_message("**hello**, *world*", chunk_limit=10)
2-element Vector{String}:
 "**hello**,"
 "*world*"

julia> split_message("**hello**, _*beautiful* world_", chunk_limit=15)
┌ Warning: message was forced-split to fit the desired chunk length limit 15
└ @ Main REPL[66]:28
3-element Vector{String}:
 "**hello**,"
 "_*beautiful* wo"
 "rld_"

julia> split_message("**hello**, _*beautiful* world_", chunk_limit=15, forcesplit=false)
┌ Warning: message could not be split into chunks smaller than the length limit 15
└ @ Main REPL[66]:32
2-element Vector{String}:
 "**hello**,"
 "_*beautiful* world_"

julia> split_message("**hello**\n=====\n", chunk_limit=12)
2-element Vector{String}:
 "**hello**\n=="
 "==="
  
julia> split_message("**hello**\n≡≡≡≡≡\n", chunk_limit=12, extrastyles = [r"\n≡+\n"])
2-element Vector{String}:
 "**hello**"
 "≡≡≡≡≡"
```
