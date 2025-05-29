```
crop_width_to_fit_string_in_field(str::AbstractString, field_width::Int; kwargs...) -> Int
```

Get the number of printable characters to be cropped so that the string `str` can fit in the field with size `field_width`.

# Keywords

  * `add_continuation_char::Bool`: If `true`, a continuation character is added to the cropped   string end. Notice that the returned string always has a printable width of   `field_size`.   (**Default** = `true`)
  * `add_space_in_continuation_char::Bool`: If `true`, a space is added before the   continuation character if `crop_size` is `:right`, or after the continuation character   if `crop_side` if `:left`.   (**Default** = `false`)
  * `continuation_char::Char`: The continuation character to add if the string is cropped.   (**Default** = `…`)
  * `printable_string_width::Int`: Provide the printable string width to reduce the   computational burden. If this parameters is lower than 0, the printable width is compute   internally.   (**Default** = -1)

# Extended Help

## Examples

```julia-repl
julia> crop_width_to_fit_string_in_field("This is a very long string for a very small field", 10)
40
```
