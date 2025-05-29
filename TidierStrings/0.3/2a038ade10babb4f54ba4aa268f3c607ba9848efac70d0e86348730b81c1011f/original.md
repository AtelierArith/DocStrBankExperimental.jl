```
str_to_sentence(s::AbstractString)
```

Convert the first character of each sentence in a string to upper case.

Arguments

  * `s`: Input string.

Returns A string with the first character of each sentence converted to upper case.

Examples

```jldoctest
julia> str_to_sentence("hello world!")
"Hello world!"

julia> str_to_sentence("a sentence mUst starT With A capital letter.")
"A sentence must start with a capital letter."
```
