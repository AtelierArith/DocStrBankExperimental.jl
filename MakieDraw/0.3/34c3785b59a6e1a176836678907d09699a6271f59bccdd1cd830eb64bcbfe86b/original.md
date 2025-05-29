```
GeometryCanvas{T<:GeometryBasics.Geometry} <: AbstractCanvas

GeometryCanvas{T}(; kw...)
```

A canvas for drawing GeometryBasics.jl geometries onto a Makie.jl `Axis`.

`T` must be `Point`, `LineString` or `Polygon`.

# Mouse and Key commands

  * Left click select point, or add point with property 1 if `click_property` is set.
  * Rick click select point, or add point with property 2 if `click_property` is set.
  * Middle click select point, or add point with property 3 if `click_property` is set.
  * Alt+click: delete points, dragging will click is held will continue deleting.
  * Shift+click: start new polygons and linstrings on `Polygon` and `LineString` canvas. Has no effect for `Point`.
  * Delete: delete selected points.
  * Shift+Delete: delete selected linestring/polygon.

# Keywords

  * `dragging`: an Observable{Bool}(false) to track mouse dragging.
  * `active`: an Observable{Bool}(true) to set if the canvas is active.
  * `accuracy_scale`: control how accurate selection needs to be. `1.0` by default.
  * `name`: A `Symbol`: name for the canvas. Will appear in a [`CanvasSelect`](@ref).
  * `propertynames`: names for feaure properties to create.
  * `properties`: an existin table of properties.
  * `click_property`: which property is set with left and right click, shold be a `Bool`.
  * `figure`: a figure to plot on.
  * `axis`: an axis to plot on.
  * `current_point`: an observable to track the currently focused point index.
  * `scatter_kw`: keywords to pass to `scatter`.
  * `lines_kw`: keywords to pass to `lines`.
  * `poly_kw`: keywords to pass to `poly`.
  * `current_point_kw`: keywords for the current point `scatter`.
  * `show_current_point`: whether to show the current point differently to the other.
  * `text_input`: wether to add text input boxes for property input.
