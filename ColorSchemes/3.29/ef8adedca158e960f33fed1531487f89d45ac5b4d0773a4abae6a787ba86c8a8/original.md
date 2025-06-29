```
get(cscheme::ColorScheme, inData :: Array{Number, 2}, rangescale=:clamp)
get(cscheme::ColorScheme, inData :: Array{Number, 2}, rangescale=(minVal, maxVal))
```

Return an RGB array of colors generated by applying the colorscheme to the 2D input data.

If `rangescale` is `:clamp` the colorscheme is applied to values between 0.0-1.0, and values outside this range get clamped to the ends of the colorscheme.

If `rangescale` is `:extrema`, the colorscheme is applied to the range `minimum(indata)..maximum(indata)`.

Else, if `rangescale` is `:centered`, the colorscheme is applied to the range `-maximum(abs, indata)..maximum(abs, indata)`.

TODO: this function expects the colorscheme to consist of RGB [0.0-1.0] values. It should work with more colortypes.

# Examples

```julia
img = get(colorschemes[:leonardo], rand(10,10)) # displays in Juno Plots window, but
save("testoutput.png", img)      # you'll need FileIO or similar to do this

img2 = get(colorschemes[:leonardo], 10.0 * rand(10, 10), :extrema)
img3 = get(colorschemes[:leonardo], 10.0 * rand(10, 10), (1.0, 9.0))

# Also works with PerceptualColourMaps
using PerceptualColourMaps # warning, installs PyPlot, PyCall, LaTeXStrings
img4 = get(PerceptualColourMaps.cmap("R1"), rand(10,10))

# resample an existing scheme to make a new one
get(ColorSchemes.darkrainbow, range(0.0, 1.0, length=13)) |> ColorScheme
```
