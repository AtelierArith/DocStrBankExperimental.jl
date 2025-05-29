```
string_search_per_line(str::AbstractString, r::Regex) -> Vector{NTuple{3, Int}}
```

Search for the pattern in regex `r` in each line of the string `str`, which can also be passed as a vector of string `lines`. The result will be a vector of `NTuple{3, Int}` with the line, beginning of the match in this line, and its length, where the two last values are related to the width of printable characters.
