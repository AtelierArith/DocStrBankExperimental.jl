```
contourf(xs, ys, zs; kwargs...)
```

Plots a filled contour of the height information in `zs` at horizontal grid positions `xs` and vertical grid positions `ys`.

The attribute `levels` can be either

  * an `Int` that produces n equally wide levels or bands
  * an `AbstractVector{<:Real}` that lists n consecutive edges from low to high, which result in n-1 levels or bands

You can also set the `mode` attribute to `:relative`. In this mode you specify edges by the fraction between minimum and maximum value of `zs`. This can be used for example to draw bands for the upper 90% while excluding the lower 10% with `levels = 0.1:0.1:1.0, mode = :relative`.

In :normal mode, if you want to show a band from `-Inf` to the low edge, set `extendlow` to `:auto` for the same color as the first level, or specify a different color (default `nothing` means no extended band) If you want to show a band from the high edge to `Inf`, set `extendhigh` to `:auto` for the same color as the last level, or specify a different color (default `nothing` means no extended band).

If `levels` is an `Int`, the contour plot will be rectangular as all `zs` will be covered. This is why `Axis` defaults to tight limits for such contourf plots. If you specify `levels` as an `AbstractVector{<:Real}`, however, note that the axis limits include the default margins because the contourf plot can have an irregular shape. You can use `tightlimits!(ax)` to tighten the limits similar to the `Int` behavior.

## Attributes

Available attributes and their defaults for `MakieCore.Plot{Makie.contourf}` are: 

```
  colormap      :viridis
  colorscale    identity
  extendhigh    "nothing"
  extendlow     "nothing"
  inspectable   true
  levels        10
  mode          :normal
  nan_color     :transparent
  transparency  false
```
