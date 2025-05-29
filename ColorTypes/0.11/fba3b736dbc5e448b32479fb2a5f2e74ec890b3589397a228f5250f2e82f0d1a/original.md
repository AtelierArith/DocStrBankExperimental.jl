```
CT = color_type(C::Type)
CT = color_type(c::Colorant)
```

Return the type of the Color object, discarding any alpha channel. For example,

```
color_type(RGB)          === RGB
color_type(RGB{Float32}) === RGB{Float32}
color_type(ARGB{N0f8})   === RGB{N0f8}
color_type(RGB(1,0,0))   === RGB{N0f8}
```

`color_type`, and related functions like [`base_color_type`](@ref), [`base_colorant_type`](@ref), and [`ccolor`](@ref) are useful for manipulating types when writing generic code.
