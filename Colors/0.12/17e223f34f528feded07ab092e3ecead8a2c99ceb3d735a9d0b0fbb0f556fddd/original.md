```
diverging_palette(h1, h2, N::Int=100; <keyword arguments>)
```

Create diverging palettes by combining 2 sequential palettes

# Arguments

  * N        - number of colors
  * h1       - the main hue of the left side [0,360]
  * h2       - the main hue of the right side [0,360]
  * c        - the overall lightness contrast [0,1]
  * s        - saturation [0,1]
  * b        - brightness [0,1]
  * w        - cold/warm parameter, i.e. the strength of the starting color [0,1]
  * d1       - depth of the ending color in the left side [0,1]
  * d2       - depth of the ending color in the right side [0,1]
  * wcolor   - starting color (warmness)
  * dcolor1  - ending color of the left side (depth)
  * dcolor2  - ending color of the right side (depth)
  * logscale - true/false for toggling logspacing
