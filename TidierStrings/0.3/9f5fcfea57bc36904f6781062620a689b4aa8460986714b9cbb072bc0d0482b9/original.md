```
word(string::AbstractString, start_index::Int=1, end_index::Int=start_index, sep::AbstractString=" ")
```

Extract a word from a string.

Arguments

  * `string`: Input string.
  * `start_index`: The starting index of the word. Default is 1.
  * `end_index`: The ending index of the word. Default is `start_index`.
  * `sep`: The separator between the start and end indices. Default is a space.

Returns The extracted word from the string.

Examples

```jldoctest
julia> word("Jane saw a cat", 1)
1-element Vector{SubString{String}}:
 "Jane"

julia> word("Jane saw a cat", 2)
1-element Vector{SubString{String}}:
 "saw"

julia> word("Jane saw a cat", -1)
1-element Vector{SubString{String}}:
 "cat"

julia> word("Jane saw a cat", 2, -1)
3-element Vector{SubString{String}}:
 "saw"
 "a"
 "cat"
```
