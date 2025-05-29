```
colorsigned()
colorsigned(colorneg, colorpos) -> f
colorsigned(colorneg, colorcenter, colorpos) -> f
```

Define a function that maps negative values (in the range [-1,0]) to the linear colormap between `colorneg` and `colorcenter`, and positive values (in the range [0,1]) to the linear colormap between `colorcenter` and `colorpos`.

The default colors are:

  * `colorcenter`: white
  * `colorneg`: green1
  * `colorpos`: magenta

See also: [`scalesigned`](@ref).
