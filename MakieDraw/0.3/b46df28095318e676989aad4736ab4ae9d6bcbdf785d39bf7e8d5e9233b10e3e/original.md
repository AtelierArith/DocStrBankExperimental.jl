```
PaintCanvas <: AbstractCanvas

PaintCanvas(; kw...)
PaintCanvas(f, data; kw...)
```

A canvas for painting into a Matrix Real numbers or colors.

# Arguments

  * `data`: an `AbstractMatrix` that will plot with `Makie.image!`, or your function `f`
  * `f`: a function, like `image!` or `heatmap!,` that will plot `f(axis, dimsions..., data)` onto `axis`.

# Keywords

  * `dimension`: the dimesion ticks of data. `axes(data)` by default.
  * `drawing`: an Observable{Bool}(false) to track if drawing is occuring.
  * `drawbutton`: the currently clicked mouse button while drawing, e.g. Mouse.left.
  * `active`: an Observable{Bool}(true) to set if the canvas is active.
  * `name`: A `Symbol`: name for the canvas. Will appear in a [`CanvasSelect`](@ref).
  * `figure`: a figure to plot on.
  * `axis`: an axis to plot on.
  * `fill_left`: Observable value for left click drawing.
  * `fill_right`: Observable value for right click drawing.
  * `fill_middle`: Observable value for middle click drawing.

# Mouse and Key commands

  * Left click/drag: draw with value of `fill_left`
  * Right click/drag: draw with value of `fill_right`
  * Middle click/drag: draw with value of `fill_middle`
