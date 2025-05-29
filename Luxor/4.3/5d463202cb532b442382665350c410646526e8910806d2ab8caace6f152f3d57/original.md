```
background(col::Colors.Colorant)
```

Paint the drawing (or the current clipping region, if there is one) with the `color``. Previously-drawn graphics will be wholly or partly obscured depending on the opacity of the color.

Returns a tuple `(r, g, b, a)` of the color that was used to paint the background.

The macros `@png`, `@draw`, and `@svg` use `background("white")` as part of the drawing set-up.

# Examples:

```julia
background("antiquewhite")
background(1, 0.0, 1.0)
background(1, 0.0, 1.0, .5)
background(Luxor.Colors.RGB(0, 1, 0))
```

If Colors.jl has been imported:

```julia
background(RGB(0, 1, 0))
background(RGBA(0, 1, 0))
background(RGBA(0, 1, 0, .5))
background(Luv(20, -20, 30))
```

If you don't specify a background color for a PNG drawing, the background will be transparent. You can set a partly or completely transparent background for PNG files by passing a color with an alpha value, such as this 'transparent black':

```julia
background(RGBA(0, 0, 0, 0))
```

or

```julia
background(0, 0, 0, 0)
```

Returns a tuple `(r, g, b, a)` of the color that was used to paint the background.
