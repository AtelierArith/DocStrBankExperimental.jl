```
NCharSpace{N}
```

A characterspace, encoding substrings `::String` as tokens `::Int`. `N` is an integer parameter: the length of encoded substrings in characters.

# Fields

  * `charmap::Vector{String}` maps tokens to substrings `W.charmap[token]` gives `substring`
  * `tokenmap::Dict{String, Int}` maps substrings to assigned tokens `W.tokenmap[substring]` gives `token`
  * `units::Vector{String}` stores the most reduced version of encoded substrings
  * `unit_length::Int` stores the length of an individual unit
  * `linear::LinearIndices` maps a composite n-token to n unit tokens
  * `cartesian::CartesianIndices` maps n unit tokens to a single composite n-token
  * `size::Int` is the number of encoded substrings / the number of tokens
  * `tokens::Vector{Int}` stores all of the encoding tokens, used for iteration
