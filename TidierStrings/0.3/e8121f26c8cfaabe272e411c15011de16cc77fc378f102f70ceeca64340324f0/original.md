str*extract*all(strings, pattern::Union{String, Regex}; captures::Bool)

Extract all occurrences of a pattern from a string

# Arguments

  * `strings`: A string to search for matches.
  * `pattern`: The pattern to search for, either as a String or a Regex.
  * `captures`: If true, return capture groups instead of the match.

# Examples

```jldoctest julia> str*extract*all("hello world hello universe hello goodbye", r"hello") 3-element Vector{String}:  "hello"  "hello"  "hello"
