```
right_crop(str::AbstractString, crop_width::Int; kwargs...) -> String, String
```

Return a string obtained by cropping the right characters of `str` given a field with a printable width of `crop_width`.

# Returns

  * `String`: Cropped string.
  * `String`: ANSI escape sequence (non-printable string) in the cropped part.

# Keyword

  * `keep_escape_seq::Bool`: If `false`, the ANSI escape sequence in the cropped field will   not be computed. In this case, the second argument returned is always empty.   (**Default** = `true`)
  * `printable_string_width::Int`: Provide the printable string width to reduce the   computational burden. If this parameters is lower than 0, the printable width is compute   internally. (**Default** = -1)

!!! warning
    If the keyword `keep_escape_seq` is set to `true`, all the string must be processed, which can lead to a substantial increase in computational time.


# Examples

```julia-repl
julia> right_crop("[1mPlease, crop this [0mstring.", 8)
("[1mPlease, crop this", "[0m")

julia> right_crop("[1mPlease, crop this [0mstring.", 8; keep_escape_seq = false)
("[1mPlease, crop this", "")
```
