```
make_colorscheme(f1::Function, f2::Function, f3::Function, f4::Function;
    model    = :RGBA,
    length   = 100,
    category = "",
    notes    = "functional ColorScheme")
```

Make a colorscheme with transparency using functions. Each argument is a function that returns a value for the red, green, blue, and alpha components for the values between 0 and 1.

`model` is the color model, and can be `:RGBA`, `:HSVA`, or `:LCHabA`.

Use `length` keyword to set the number of colors in the colorscheme.

The default color mo            del is `:RGBA`, and the functions should return values in the appropriate range:

  * f1 - [0.0 - 1.0]   - red
  * f2 - [0.0 - 1.0]   - green
  * f3 - [0.0 - 1.0]   - blue
  * f4 - [0.0 - 1.0]   - alpha

For the `:HSVA` color model:

  * f1 - [0.0 - 360.0] - hue
  * f2 - [0.0 - 1.0]   - saturataion
  * f3 - [0.0 - 1.0]   - value (brightness)
  * f4 - [0.0 - 1.0]   - alpha

For the `:LCHabA` color model:

  * f1 - [0.0 - 100.0] - luminance
  * f2 - [0.0 - 100.0] - chroma
  * f3 - [0.0 - 360.0] - hue
  * f4 - [0.0 - 1.0]   - alpha

## Examples

```julia
csa = make_colorscheme1(
    n -> red(get(ColorSchemes.leonardo, n)),
    n -> green(get(ColorSchemes.leonardo, n)),
    n -> blue(get(ColorSchemes.leonardo, n)),
    n -> 1 - identity(n))
```
