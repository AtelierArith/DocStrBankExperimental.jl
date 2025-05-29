```
highlight_search(str::AbstractString, search_matches::Vector{Tuple{Int, Int}}; kwargs...) -> String
highlight_search(str::AbstractString, regex::Regex; kwargs...) -> String
```

Return the text in the string `str` with the `search_matches` (see [`string_search`](@ref)) highlighted. If a `regex` is passed in the place of `search_matches`, the latter is automatically computed using [`string_search`](@ref).

# Keywords

  * `active_match::Int`: The match number that is considered active. This match is highlighted   using `active_highlight` instead of `highlight`.   (**Default** = 0)
  * `active_highlight::String`: ANSI escape sequence that contains the decoration of the   active highlight.   (**Default** = `\e[30;43m`.)
  * `highlight::String`: ANSI escape sequence that contains the decoration of the highlight.   (**Default** = `\e[7m`)
  * `max_column::Int`: Stop processing if the match is after this column. If it is equal or   lower than 0, this limit will not be considered.   (**Default** = 0)
  * `min_column::Int`: Do not process matches before this column. If it is equal or lower than   0, this limit will not be considered.   (**Default** = 0)
  * `start_column::Int`: The algorithm will consider that the first character in `str` is in   this column.   (**Default** = 1)
