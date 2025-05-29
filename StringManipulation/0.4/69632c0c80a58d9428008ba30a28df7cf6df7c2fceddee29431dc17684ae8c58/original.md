```
align_string(str::AbstractString, field_width::Int, alignment::Symbol; kwargs...) -> String
```

Align the string `str` in the field with width `field_width` using `alignment`, which can be:

  * `:l`: Align the string to the left;
  * `:c`: Align the string in the center;
  * `:r`: Align the string in the right.

!!! note
    If the printable width of `str` is higher than `field_width`, nothing will be changed.


!!! note
    This function treats `\n` as a normal characters. If one wants to align every line, use the function [`align_string_per_line`](@ref).


# Keyword

  * `fill::Bool`: If `true`, the string will be filled with spaces to the right so that the   resulting string has printable width `field_size` if the initial string printable width   is lower than it.   (**Default** = `false`)
  * `printable_string_width::Int`: Provide the printable string width to reduce the   computational burden. If this parameters is lower than 0, the printable width is compute   internally.   (**Default** = -1)

# Extended Help

## Examples

```julia-repl
julia> align_string("My String", 92, :c) |> println
                                         My String

julia> align_string("My String", 92, :l) |> println
My String

julia> align_string("My String", 92, :r) |> println
                                                                                   My String
```
