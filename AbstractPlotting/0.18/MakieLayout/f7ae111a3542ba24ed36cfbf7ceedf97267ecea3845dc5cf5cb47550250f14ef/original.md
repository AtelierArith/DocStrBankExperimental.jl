```
Colorbar(parent; kwargs...)
Colorbar(parent, plotobject; kwargs...)
Colorbar(parent, heatmap::Heatmap; kwargs...)
Colorbar(parent, contourf::Contourf; kwargs...)
```

Add a Colorbar to `parent`. If you pass a `plotobject`, a `heatmap` or `contourf`, the Colorbar is set up automatically such that it tracks these objects' relevant attributes like `colormap`, `colorrange`, `highclip` and `lowclip`. If you want to adjust these attributes afterwards, change them in the plot object, otherwise the Colorbar and the plot object will go out of sync.

Colorbar has the following attributes:

`alignmode`
Default: `Inside()`
The align mode of the colorbar in its parent GridLayout.

`bottomspinecolor`
Default: `RGBf0(0, 0, 0)`
The color of the bottom spine.

`bottomspinevisible`
Default: `true`
Controls if the bottom spine is visible.

`colormap`
Default: `lift_parent_attribute(scene, :colormap, :viridis)`
The colormap that the colorbar uses.

`flip_vertical_label`
Default: `false`
Flips the colorbar label if the axis is vertical.

`flipaxis`
Default: `true`
Flips the axis to the right if vertical and to the top if horizontal.

`halign`
Default: `:center`
The horizontal alignment of the colorbar in its suggested bounding box.

`height`
Default: `AbstractPlotting.automatic`
The height setting of the colorbar.

`highclip`
Default: `nothing`
The color of the high clip triangle.

`label`
Default: `""`
The color bar label string.

`labelcolor`
Default: `lift_parent_attribute(scene, :textcolor, :black)`
The label color.

`labelfont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The label font family.

`labelpadding`
Default: `5.0`
The gap between the label and the ticks.

`labelsize`
Default: `lift_parent_attribute(scene, :fontsize, 16.0f0)`
The label font size.

`labelvisible`
Default: `true`
Controls if the label is visible.

`leftspinecolor`
Default: `RGBf0(0, 0, 0)`
The color of the left spine.

`leftspinevisible`
Default: `true`
Controls if the left spine is visible.

`limits`
Default: `(0.0f0, 1.0f0)`
The range of values depicted in the colorbar.

`lowclip`
Default: `nothing`
The color of the low clip triangle.

`minortickalign`
Default: `0.0`
The alignment of minor ticks on the axis spine

`minortickcolor`
Default: `:black`
The tick color of minor ticks

`minorticks`
Default: `IntervalsBetween(5)`
The tick locator for the minor ticks

`minorticksize`
Default: `4.0`
The tick size of minor ticks

`minorticksvisible`
Default: `false`
Controls if minor ticks are visible

`minortickwidth`
Default: `1.0`
The tick width of minor ticks

`nsteps`
Default: `100`
The number of steps in the heatmap underlying the colorbar gradient.

`rightspinecolor`
Default: `RGBf0(0, 0, 0)`
The color of the right spine.

`rightspinevisible`
Default: `true`
Controls if the right spine is visible.

`scale`
Default: `identity`
The axis scale

`size`
Default: `16`
The width or height of the colorbar, depending on if it's vertical or horizontal, unless overridden by `width` / `height`

`spinewidth`
Default: `1.0`
The line width of the spines.

`tellheight`
Default: `true`
Controls if the parent layout can adjust to this element's height

`tellwidth`
Default: `true`
Controls if the parent layout can adjust to this element's width

`tickalign`
Default: `0.0`
The alignment of the tick marks relative to the axis spine (0 = out, 1 = in).

`tickcolor`
Default: `RGBf0(0, 0, 0)`
The color of the tick marks.

`tickformat`
Default: `AbstractPlotting.automatic`
Format for ticks.

`ticklabelalign`
Default: `AbstractPlotting.automatic`
The horizontal and vertical alignment of the tick labels.

`ticklabelcolor`
Default: `lift_parent_attribute(scene, :textcolor, :black)`
The color of the tick labels.

`ticklabelfont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The font family of the tick labels.

`ticklabelpad`
Default: `3.0`
The gap between tick labels and tick marks.

`ticklabelrotation`
Default: `0.0`
The rotation of the ticklabels

`ticklabelsize`
Default: `lift_parent_attribute(scene, :fontsize, 16.0f0)`
The font size of the tick labels.

`ticklabelspace`
Default: `AbstractPlotting.automatic`
The space reserved for the tick labels.

`ticklabelsvisible`
Default: `true`
Controls if the tick labels are visible.

`ticks`
Default: `AbstractPlotting.automatic`
The ticks.

`ticksize`
Default: `6.0`
The size of the tick marks.

`ticksvisible`
Default: `true`
Controls if the tick marks are visible.

`tickwidth`
Default: `1.0`
The line width of the tick marks.

`topspinecolor`
Default: `RGBf0(0, 0, 0)`
The color of the top spine.

`topspinevisible`
Default: `true`
Controls if the top spine is visible.

`valign`
Default: `:center`
The vertical alignment of the colorbar in its suggested bounding box.

`vertical`
Default: `true`
Controls if the colorbar is oriented vertically.

`width`
Default: `AbstractPlotting.automatic`
The width setting of the colorbar. Use `size` to set width or height relative to colorbar orientation instead.
