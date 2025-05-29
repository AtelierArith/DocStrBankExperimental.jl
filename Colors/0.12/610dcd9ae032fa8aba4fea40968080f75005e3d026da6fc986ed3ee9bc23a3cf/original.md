```
sequential_palette(h, N::Int=100; <keyword arguments>)
```

Implements the color palette creation technique by [Wijffelaars, M., et al. (2008)](http://magnaview.nl/documents/MagnaView-M_Wijffelaars-Generating_color_palettes_using_intuitive_parameters.pdf).

Colormaps are formed using Bézier curves in LCHuv colorspace with some constant hue. In addition, start and end points can be given that are then blended to the original hue smoothly.

# Arguments

  * N        - number of colors
  * h        - the main hue [0,360]
  * c        - the overall lightness contrast [0,1]
  * s        - saturation [0,1]
  * b        - brightness [0,1]
  * w        - cold/warm parameter, i.e. the strength of the starting color [0,1]
  * d        - depth of the ending color [0,1]
  * wcolor   - starting color (warmness)
  * dcolor   - ending color (depth)
  * logscale - true/false for toggling logspacing
