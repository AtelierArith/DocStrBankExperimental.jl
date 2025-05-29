```
align_string_per_line(str::AbstractString, field_width::Int, alignment::Symbol; kwargs...) -> String
```

Align each line of the string `str` in the field with width `field_width` using `alignment`, which can be:

  * `:l`: Align the string to the left;
  * `:c`: Align the string in the center;
  * `:r`: Align the string in the right.

!!! note
    If the printable width of `str` is higher than `field_width`, nothing will be changed.


# Keyword

  * `fill::Bool`: If `true`, the string will be filled with spaces to the right so that the   resulting string has printable width `field_size` if the initial string printable width   is lower than it.   (**Default** = `false`)

# Extended Help

## Examples

```julia-repl
julia> align_string_per_line("""
       This is a string
       with multiple
       lines.""", 92, :c) |> println
                                      This is a string
                                       with multiple
                                           lines.

julia> align_string_per_line("""
       This is a string
       with multiple
       lines.""", 92, :l) |> println
This is a string
with multiple
lines.

julia> align_string_per_line("""
       This is a string
       with multiple
       lines.""", 92, :r) |> println
                                                                            This is a string
                                                                               with multiple
                                                                                      lines.
```
