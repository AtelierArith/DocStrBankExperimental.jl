```
left_crop(str::AbstractString, crop_width::Int) -> String, String
```

Return a string obtained by cropping the left characters of `str` so that its printable width is reduced by `crop_width` display units.

# Returns

  * `String`: ANSI escape sequence (non-printable string) in the cropped part.
  * `String`: Cropped string.

# Extended Help

## Examples

```julia-repl
julia> left_crop("\e[1mPlease, crop this string.", 8)
("\e[1m", "crop this string.")
```
