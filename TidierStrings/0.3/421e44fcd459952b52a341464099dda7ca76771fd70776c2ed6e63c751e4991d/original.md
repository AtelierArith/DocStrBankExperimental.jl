str_trunc(string::AbstractString, width::Integer; side::String="right", ellipsis::AbstractString="...")

Truncate a string to a fixed number of characters.

# Arguments

  * `string`: Input string to be truncated.
  * `width`: Maximum width of the resulting string, including the ellipsis.
  * `side`: Side from which to truncate. Can be "right", "left", or "center". Defaults to "right".
  * `ellipsis`: String to indicate content has been removed. Defaults to "...".

# Returns

A truncated string of length less than or equal to `width`, including the ellipsis.

# Examples

```jldoctest
julia> str_trunc("This is a long string", 10)
"This is..."

julia> str_trunc("This is a long string", 10, side="left")
"...g string"

julia> str_trunc("This is a long string", 10, side="center")
"Thi...ring"

julia> str_trunc("Short", 10)
"Short"

julia> str_trunc("This is a long string that needs to be truncated", 20, side = "right", ellipsis = "--")
"This is a long str--"
```
