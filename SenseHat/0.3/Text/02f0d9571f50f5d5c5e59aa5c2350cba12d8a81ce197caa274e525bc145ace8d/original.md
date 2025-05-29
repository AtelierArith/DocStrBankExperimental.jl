```
show_message(s::String, speed::Real = 0.2, color::ColorTypes.AbstractRGB = colorant"white")
```

Display a scrolling message `s` on the `SenseHat` LED Matrix. `speed` is the time in seconds per frame and `color` is the color of text.

# Example

```
using SenseHat

show_message("Hello, World!", 0.2, colorant"purple")
```
