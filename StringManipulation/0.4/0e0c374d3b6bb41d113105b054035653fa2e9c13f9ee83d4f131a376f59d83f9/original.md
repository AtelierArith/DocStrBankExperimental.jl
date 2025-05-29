```
padding_for_string_alignment(str::AbstractString, field_width::Int, alignment::Symbol; kwargs...) -> Union{Nothing, NTuple{2, Int}}
```

Return the left and right padding required to align the string `str` in a field with width `field_width` using the `alignment`, which can be:

  * `:l`: Align the string to the left;
  * `:c`: Align the string in the center;
  * `:r`: Align the string in the right.

This function can return `nothing` in the following conditions:

1. The string does not need to be modified;
2. The alignment symbol is unknown; or
3. The printable width of `str` is longer than `field_width`.

!!! note
    This function treats `\n` as a normal characters.


# Keyword

  * `fill::Bool`: If `true`, the string will be filled with spaces to the right so that the   resulting string has printable width `field_size` if the initial string printable width   is lower than it.   (**Default** = `false`)
  * `printable_string_width::Int`: Provide the printable string width to reduce the   computational burden. If this parameters is lower than 0, the printable width is compute   internally.   (**Default** = -1)

# Extended Help

## Examples

```julia-repl
julia> padding_for_string_alignment("My string", 92, :c)
(41, 0)

julia> padding_for_string_alignment("My string", 92, :l)

julia> padding_for_string_alignment("My string", 92, :r)
(83, 0)
```
