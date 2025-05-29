```
str_trim(s::AbstractString, side::String="both")
```

Removes all whitespace from the string `s` on the left and right side, or on both sides if `side` is "both".

Arguments

  * `s`: Input string.
  * `side`: The side(s) from which to remove whitespace. Can be "left", "right", or "both".

Returns The string `s` with all whitespace removed on the left and right side, or on both sides if `side` is "both".

Examples

```jldoctest
julia> str_trim("  hello world! 😊  ")
"hello world! 😊"
```
