```
image(x, y, image)
image(image)
```

Plots an image on a rectangle bounded by `x` and `y` (defaults to size of image).

## Plot type

The plot type alias for the `image` function is `Image`.

## Attributes

**`alpha`** =  `1.0`  — The alpha value of the colormap or color attribute. Multiple alphas like in `plot(alpha=0.2, color=(:red, 0.5)`, will get multiplied.

**`clip_planes`** =  `automatic`  — Clip planes offer a way to do clipping in 3D space. You can set a Vector of up to 8 `Plane3f` planes here, behind which plots will be clipped (i.e. become invisible). By default clip planes are inherited from the parent plot or scene. You can remove parent `clip_planes` by passing `Plane3f[]`.

**`colormap`** =  `[:black, :white]`  — Sets the colormap that is sampled for numeric `color`s. `PlotUtils.cgrad(...)`, `Makie.Reverse(any_colormap)` can be used as well, or any symbol from ColorBrewer or PlotUtils. To see all available color gradients, you can call `Makie.available_gradients()`.

**`colorrange`** =  `automatic`  — The values representing the start and end points of `colormap`.

**`colorscale`** =  `identity`  — The color transform function. Can be any function, but only works well together with `Colorbar` for `identity`, `log`, `log2`, `log10`, `sqrt`, `logit`, `Makie.pseudolog10` and `Makie.Symlog10`.

**`depth_shift`** =  `0.0`  — Adjusts the depth value of a plot after all other transformations, i.e. in clip space, where `-1 <= depth <= 1`. This only applies to GLMakie and WGLMakie and can be used to adjust render order (like a tunable overdraw).

**`fxaa`** =  `false`  — Adjusts whether the plot is rendered with fxaa (anti-aliasing, GLMakie only).

**`highclip`** =  `automatic`  — The color for any value above the colorrange.

**`inspectable`** =  `@inherit inspectable`  — Sets whether this plot should be seen by `DataInspector`. The default depends on the theme of the parent scene.

**`inspector_clear`** =  `automatic`  — Sets a callback function `(inspector, plot) -> ...` for cleaning up custom indicators in DataInspector.

**`inspector_hover`** =  `automatic`  — Sets a callback function `(inspector, plot, index) -> ...` which replaces the default `show_data` methods.

**`inspector_label`** =  `automatic`  — Sets a callback function `(plot, index, position) -> string` which replaces the default label generated by DataInspector.

**`interpolate`** =  `true`  — Sets whether colors should be interpolated between pixels.

**`lowclip`** =  `automatic`  — The color for any value below the colorrange.

**`model`** =  `automatic`  — Sets a model matrix for the plot. This overrides adjustments made with `translate!`, `rotate!` and `scale!`.

**`nan_color`** =  `:transparent`  — The color for NaN values.

**`overdraw`** =  `false`  — Controls if the plot will draw over other plots. This specifically means ignoring depth checks in GL backends

**`space`** =  `:data`  — Sets the transformation space for box encompassing the plot. See `Makie.spaces()` for possible inputs.

**`ssao`** =  `false`  — Adjusts whether the plot is rendered with ssao (screen space ambient occlusion). Note that this only makes sense in 3D plots and is only applicable with `fxaa = true`.

**`transformation`** =  `:automatic`  — *No docs available.*

**`transparency`** =  `false`  — Adjusts how the plot deals with transparency. In GLMakie `transparency = true` results in using Order Independent Transparency.

**`uv_transform`** =  `automatic`  — Sets a transform for uv coordinates, which controls how the image is mapped to its rectangular area. The attribute can be `I`, `scale::VecTypes{2}`, `(translation::VecTypes{2}, scale::VecTypes{2})`, any of :rotr90, :rotl90, :rot180, :swap*xy/:transpose, :flip*x, :flip*y, :flip*xy, or most generally a `Makie.Mat{2, 3, Float32}` or `Makie.Mat3f` as returned by `Makie.uv_transform()`. They can also be changed by passing a tuple `(op3, op2, op1)`.

**`visible`** =  `true`  — Controls whether the plot will be rendered or not.
