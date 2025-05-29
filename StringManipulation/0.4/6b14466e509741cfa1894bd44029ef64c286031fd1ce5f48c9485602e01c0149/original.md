```
fit_string_in_field(str::AbstractString, field_width::Int; kwargs...) -> String
```

Crop the string `str` to fit within a field of width `field_width`.

# Keywords

  * `add_continuation_char::Bool`: If `true`, a continuation character is added to the cropped   string end. Notice that the returned string always has a printable width of   `field_size`.   (**Default** = `true`)
  * `add_space_in_continuation_char::Bool`: If `true`, a space is added before the   continuation character if `crop_size` is `:right`, or after the continuation character   if `crop_side` if `:left`.   (**Default** = `false`)
  * `continuation_char::Char`: The continuation character to add if the string is cropped.   (**Default** = `…`)
  * `crop_side::Symbol`: Select from which side the characters must be removed to fit the   string into the field. It can be `:right` or `:left`.   (**Default** = `:right`)
  * `field_margin::Int`: Consider an additional margin in the field if it must be cropped.   (**Default** = 0)
  * `keep_escape_seq::Bool`: If `true`, the ANSI escape sequences found in the cropped part   will be kept.   (**Default** = `true`)
  * `printable_string_width::Int`: Provide the printable string width to reduce the   computational burden. If this parameters is lower than 0, the printable width is compute   internally.   (**Default** = -1)

# Extended Help

## Examples

```julia-repl
julia> fit_string_in_field("This is a very long string for a very small field", 10)
"This is a…"

julia> fit_string_in_field("This is a very long string for a very small field", 10; crop_side = :left)
"…all field"
```
