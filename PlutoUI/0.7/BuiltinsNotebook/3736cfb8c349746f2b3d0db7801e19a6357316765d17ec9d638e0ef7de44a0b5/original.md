A color input - the user can pick an RGB color, the color is returned as a `Colorant`, a type from the package [Colors.jl](https://github.com/JuliaGraphics/Colors.jl).

Use `default` to set the initial value.

# Examples

```julia
@bind color1 ColorPicker()
```

```julia
using Colors

@bind color2 ColorPicker(default=colorant"#aabbcc")
```
