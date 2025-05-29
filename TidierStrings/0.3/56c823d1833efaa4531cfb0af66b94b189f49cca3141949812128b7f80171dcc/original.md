```
str_pad(string::AbstractString, width::Integer; side::String="right", pad::AbstractString=" ", use_width::Bool=true)
```

Pad a string to a certain width.

# Returns

The padded string.

# Arguments

  * `string`: The string to be padded.
  * `width`: The width to pad the string to.
  * `side`: The side to pad the string on. Can be "left", "right", or "both".
  * `pad`: The string to use for padding.
  * `use_width`: Whether to use the width argument or the length of the string.

# Examples

```jldoctest
julia> str_pad("hello", 10)
"hello     "

julia> str_pad("hello", 10, side="left")
"     hello"

julia> str_pad("hello", 10, side="both")
"  hello   "

julia> str_pad("hello", 10, side="both", pad="*")
"**hello***"
```
