```
get_height(font::MonospaceBitmapASCIIFont)
```

Return the height of a glyph contained in the monospace font `font` along the i-axis (vertical-axis, 1st-axis).

See also [`get_width`](@ref).

# Examples

```julia-repl
julia> get_height(TERMINUS_32_16)
32

julia> get_height(TERMINUS_16_8)
16
```
