```
str_to_title(s::AbstractString)
```

Convert the first character of each word in a string to upper case.

Arguments

  * `s`: Input string.

Returns A string with the first character of each word converted to upper case.

Examples

```jldoctest
julia> str_to_title("hello world!")
"Hello World!"

julia> str_to_title("This is a title")
"This Is A Title"
```
