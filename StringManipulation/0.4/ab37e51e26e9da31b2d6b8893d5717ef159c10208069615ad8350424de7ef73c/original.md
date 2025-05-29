```
highlight_search(lines::Vector{T}, search_matches::Dict{Int, Vector{Tuple{Int, Int}}}; kwargs...) where T <: AbstractString -> String
highlight_search(lines::Vector{T}, regex::Regex]; kwargs...) where T <: AbstractString -> String
```

Return the text composed of the `lines` with the `search_matches` (see [`string_search_per_line`](@ref)) highlighted. If a `regex` is passed in the place of `search_matches`, the latter is automatically computed using [`string_search_per_line`](@ref).

# Keywords

  * `active_match::Int`: The match number that is considered active. This match is highlighted   using `active_highlight` instead of `highlight`.   (**Default** = 0)
  * `active_highlight::String`: ANSI escape sequence that contains the decoration of the   active highlight.   (**Default** = `\e[30;43m`.)
  * `end_line::Int`: Line to end the processing. If it is equal or lower than 0, all lines   will be processed.   (**Default** = 0)
  * `highlight::String`: ANSI escape sequence that contains the decoration of the highlight.   (**Default** = `\e[7m`)
  * `max_column::Int`: Stop processing if the match is after this column. If it is equal or   lower than 0, this limit will not be considered.   (**Default** = 0)
  * `min_column::Int`: Do not process matches before this column. If it is equal or lower than   0, this limit will not be considered.   (**Default** = 0)
  * `start_line::Int`: Line to begin the processing.   (**Default** = 1)
