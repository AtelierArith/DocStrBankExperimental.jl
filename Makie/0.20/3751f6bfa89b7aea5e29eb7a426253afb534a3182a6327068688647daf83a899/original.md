```
tooltip(position, string)
tooltip(x, y, string)
```

Creates a tooltip pointing at `position` displaying the given `string`

## Attributes

### Generic

  * `visible::Bool = true` sets whether the plot will be rendered or not.
  * `overdraw::Bool = false` sets whether the plot will draw over other plots. This specifically means ignoring depth checks in GL backends.
  * `transparency::Bool = false` adjusts how the plot deals with transparency. In GLMakie `transparency = true` results in using Order Independent Transparency.
  * `inspectable::Bool = true` sets whether this plot should be seen by `DataInspector`.
  * `depth_shift::Float32 = 0f0` adjusts the depth value of a plot after all other transformations, i.e. in clip space, where `0 <= depth <= 1`. This only applies to GLMakie and WGLMakie and can be used to adjust render order (like a tunable overdraw).
  * `space::Symbol = :data` sets the transformation space for positions of markers. See `Makie.spaces()` for possible inputs.

### Tooltip specific

  * `offset = 10` sets the offset between the given `position` and the tip of the triangle pointing at that position.
  * `placement = :above` sets where the tooltipü should be placed relative to `position`. Can be `:above`, `:below`, `:left`, `:right`.
  * `align = 0.5` sets the alignment of the tooltip relative `position`. With `align = 0.5` the tooltip is centered above/below/left/right the `position`.
  * `backgroundcolor = :white` sets the background color of the tooltip.
  * `triangle_size = 10` sets the size of the triangle pointing at `position`.
  * `outline_color = :black` sets the color of the tooltip outline.
  * `outline_linewidth = 2f0` sets the linewidth of the tooltip outline.
  * `outline_linestyle = nothing` sets the linestyle of the tooltip outline.
  * `textpadding = (4, 4, 4, 4)` sets the padding around text in the tooltip. This is given as `(left, right, bottom top)` offsets.
  * `textcolor = theme(scene, :textcolor)` sets the text color.
  * `fontsize = 16` sets the text size.
  * `font = theme(scene, :font)` sets the font.
  * `strokewidth = 0`: Gives text an outline if set to a positive value.
  * `strokecolor = :white` sets the text outline color.
  * `justification = :left` sets whether text is aligned to the `:left`, `:center` or `:right` within its bounding box.
