```
get_width(font::MonospaceBitmapASCIIFont)
```

Return the width of a glyph contained in the monospace font `font` along the j-axis (horizontal-axis, 2nd-axis).

See also [`get_width`](@ref).

# Examples

```julia-repl
julia> get_width(TERMINUS_32_16)
16

julia> get_width(TERMINUS_16_8)
8
```
