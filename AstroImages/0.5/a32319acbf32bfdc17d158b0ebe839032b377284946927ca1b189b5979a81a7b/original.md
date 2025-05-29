```
composecolors(
    images,
    cmap=["#F00", "#0F0", "#00F"];
    clims,
    stretch,
    contrast,
    bias,
    multiplier
)
```

Create a color composite of multiple images by applying `imview` and blending the results. This function can be used to create RGB composites using any number of channels (e.g. red, green, blue, and hydrogen alpha) as well as more exotic images like blending radio and optical data using two different colormaps.

`cmap` should be a list of colorants, named colors (see Colors.jl), or colorschemes (see ColorSchemes.jl). `clims`, `stretch`, `contrast`, and `bias` are passed on to `imview`. They can be a single value or a list of different values for each image.

The headers of the returned image are copied from the first image.

Examples:

```julia
# Basic RGB
composecolors([redimage, greenimage, blueimage])
# Non-linear stretch before blending
composecolors([redimage, greenimage, blueimage], stretch=asinhstretch)
# More than three channels are allowed (H alpha in pink)
composecolors(
    [antred, antgreen, antblue, anthalp],
    ["red", "green", "blue", "maroon1"],
    multiplier=[1,2,1,1]
)
# Can mix
composecolors([radioimage, xrayimage], [:ice, :magma], clims=extrema)
composecolors([radioimage, xrayimage], [:magma, :viridis], clims=[Percent(99), Zscale()])
```
