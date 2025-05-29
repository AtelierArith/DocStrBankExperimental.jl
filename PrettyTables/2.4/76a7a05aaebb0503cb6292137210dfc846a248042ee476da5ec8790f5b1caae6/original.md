```
AnsiTextCell
```

A text cell that supports rendering ANSI escape sequences without interfering with the table layout.

# Fields

**Public**

  * `string::String`: The string with the cell text that can contain ANSI escape sequences.

**Private**

  * `_rendered_lines::Union{Nothing, Vector{String}}`: The lines with the rendered strings.
  * `_stripped_lines::Union{Nothing, Vector{String}}`: The lines with the printable text.
  * `_crops::Union{Nothing, Vector{Int}}`: Vector with the number of characters that must be   cropped at each line.
  * `_left_pads::Union{Nothing, Vector{Int}}`: Left padding to be applied to each line.
  * `_right_pads::Union{Nothing, Vector{Int}}`: Right padding to be applied to each line.
  * `_suffixes::Union{Nothing, Vector{String}}`: Suffixed to be applied to each line.
