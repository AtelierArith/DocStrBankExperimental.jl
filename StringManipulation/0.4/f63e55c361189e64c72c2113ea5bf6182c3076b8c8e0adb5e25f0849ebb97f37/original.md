```
string_search(str::AbstractString, r::Regex) -> Vector{Tuple{Int, Int}}
```

Search for the pattern in regex `r` in the string `str`. The result will be a vector of `Tuple{Int, Int}` with the beginning of the match and its length, where both values are related to the width of printable characters.
