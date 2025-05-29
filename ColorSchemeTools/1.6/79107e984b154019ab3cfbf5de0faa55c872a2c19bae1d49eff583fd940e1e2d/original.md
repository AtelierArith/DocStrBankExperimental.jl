```
equalize(cs::ColorScheme;
    colormodel::Symbol="RGB",
    formula::String="CIE76",
    W::Array=[1.0, 0.0, 0.0],
    sigma::Real=0.0,
    cyclic::Bool=false)

equalize(ca::Array{Colorant, 1}; 
    # same keywords 
    )
```

Equalize colors in the colorscheme `cs` or the array of colors `ca` so that they are more perceptually uniform.

  * `cs` is a ColorScheme
  * `ca` is an array of colors
  * `colormodel``is`:RGB`or`:LAB`
  * `formula` is "CIE76" or "CIEDE2000"
  * `W` is a vector of three weights to be applied to the lightness, chroma, and hue components of the difference equation
  * `sigma` is an optional Gaussian smoothing parameter
  * `cyclic` is a Boolean flag indicating whether the colormap is cyclic

Returns a colorscheme with the colors adjusted.
