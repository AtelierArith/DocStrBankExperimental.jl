```
make_colorscheme(f1::Function, f2::Function, f3::Function;
    model    = :RGB,
    length   = 100,
    category = "",
    notes    = "functional ColorScheme")
```

Make a colorscheme using functions. Each argument is a function that returns a value for the red, green, and blue components for the values between 0 and 1.

`model` is the color model, and can be `:RGB`, `:HSV`, or `:LCHab`.

Use `length` keyword to set the number of colors in the colorscheme.

The default color model is `:RGB`, and the functions should return values in the appropriate range:

  * f1 - [0.0 - 1.0]   - red
  * f2 - [0.0 - 1.0]   - green
  * f3 - [0.0 - 1.0]   - blue

For the `:HSV` color model:

  * f1 - [0.0 - 360.0] - hue
  * f2 - [0.0 - 1.0]   - saturataion
  * f3 - [0.0 - 1.0]   - value (brightness)

For the `:LCHab` color model:

  * f1 - [0.0 - 100.0] - luminance
  * f2 - [0.0 - 100.0] - chroma
  * f3 - [0.0 - 360.0] - hue

### Example

Make a colorscheme with the red component defined as a sine curve running  from 0 to π and back to 0, the green component is always 0, and the blue component starts at π and goes to 0 at 0.5 (it's clamped to 0 after that).

```julia
make_colorscheme(n -> sin(n * π), n -> 0, n -> cos(n * π))
```
