```
Cbase = base_color_type(C::Type)
Cbase = base_color_type(c::Colorant)
```

Return the Color type without alpha channel or a specified numeric element type. `base_color_type` is similar to [`color_type`](@ref), except it "strips off" the element type. It always returns a parametric type, which makes it convenient for switching the numeric element type.

For example, compare

```
base_color_type(RGB{N0f8})  === RGB
base_color_type(RGBA{N0f8}) === RGB
```

vs

```
color_type(RGB{N0f8})       === RGB{N0f8}
```

Switching element types can be done as follows:

```
c64 = base_color_type(c){Float64}(color(c))
```

`base_color_type` discards any alpha channel. See [`base_colorant_type`](@ref) if you want to preserve the alpha channel.
