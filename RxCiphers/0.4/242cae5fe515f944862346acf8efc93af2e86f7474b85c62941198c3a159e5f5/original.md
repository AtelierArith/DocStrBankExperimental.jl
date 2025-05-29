```
DLMSpace
```

A characterspace, encoding substrings `::String` as tokens `::Int`. `dlm` is the delimiter, separating substrings to be tokenised.

# Fields

  * `charmap::Vector{String}` maps tokens to substrings `W.charmap[token]` gives `substring`
  * `tokenmap::Dict{String, Int}` maps substrings to assigned tokens `W.tokenmap[substring]` gives `token`
  * `dlm` is the delimiting string/character
  * `size::Int` is the number of encoded substrings / the number of tokens
  * `tokens::Vector{Int}` stores all of the encoding tokens, used for iteration
