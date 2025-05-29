```
str_extract(string, pattern::Union{String, Regex})
```

Extract the first occurrence of a pattern from a string

# Arguments

  * `strings`: A string to search for matches.
  * `pattern`: The pattern to search for, either as a String or a Regex.

# Examples

```jldoctest julia> str_extract("hello world hello universe hello goodbye", r"hello") "hello"

julia> str_extract.(["hello world", "hello universe", "goodbye"], "hello") 3-element Vector{Union{Missing, String}}:  "hello"  "hello"  missing  ```
