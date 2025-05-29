Axis has the following attributes:

`alignmode`
Default: `Inside()`
The align mode of the axis in its parent GridLayout.

`aspect`
Default: `nothing`
The forced aspect ratio of the axis. `nothing` leaves the axis unconstrained, `DataAspect()` forces the same ratio as the ratio in data limits between x and y axis, `AxisAspect(ratio)` sets a manual ratio.

`autolimitaspect`
Default: `nothing`
Constrains the data aspect ratio (`nothing` leaves the ratio unconstrained).

`backgroundcolor`
Default: `:white`
The background color of the axis.

`bottomspinecolor`
Default: `:black`
The color of the bottom axis spine.

`bottomspinevisible`
Default: `true`
Controls if the bottom axis spine is visible.

`flip_ylabel`
Default: `false`
Controls if the ylabel's rotation is flipped.

`halign`
Default: `:center`
The horizontal alignment of the axis within its suggested bounding box.

`height`
Default: `nothing`
The height of the axis.

`leftspinecolor`
Default: `:black`
The color of the left axis spine.

`leftspinevisible`
Default: `true`
Controls if the left axis spine is visible.

`limits`
Default: `(nothing, nothing)`
The limits that the user has manually set. They are reinstated when calling `reset_limits!` and are set to nothing by `autolimits!`. Can be either a tuple (xlow, xhigh, ylow, high) or a tuple (nothing*or*xlims, nothing*or*ylims). Are set by `xlims!`, `ylims!` and `limits!`.

`palette`
Default: `if scene !== nothing && haskey(scene.attributes, :palette)     deepcopy(scene.palette) else     Attributes() end`
Attributes with one palette per key, for example `color = [:red, :green, :blue]`

`panbutton`
Default: `AbstractPlotting.Mouse.right`
The button for panning.

`rightspinecolor`
Default: `:black`
The color of the right axis spine.

`rightspinevisible`
Default: `true`
Controls if the right axis spine is visible.

`spinewidth`
Default: `1.0`
The width of the axis spines.

`tellheight`
Default: `true`
Controls if the parent layout can adjust to this element's height

`tellwidth`
Default: `true`
Controls if the parent layout can adjust to this element's width

`title`
Default: `""`
The axis title string.

`titlealign`
Default: `:center`
The horizontal alignment of the title.

`titlecolor`
Default: `lift_parent_attribute(scene, :textcolor, :black)`
The color of the title

`titlefont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The font family of the title.

`titlegap`
Default: `4.0`
The gap between axis and title.

`titlesize`
Default: `lift_parent_attribute(scene, :fontsize, 16.0f0)`
The title's font size.

`titlevisible`
Default: `true`
Controls if the title is visible.

`topspinecolor`
Default: `:black`
The color of the top axis spine.

`topspinevisible`
Default: `true`
Controls if the top axis spine is visible.

`valign`
Default: `:center`
The vertical alignment of the axis within its suggested bounding box.

`width`
Default: `nothing`
The width of the axis.

`xautolimitmargin`
Default: `(0.05f0, 0.05f0)`
The relative margins added to the autolimits in x direction.

`xaxisposition`
Default: `:bottom`
The position of the x axis (`:bottom` or `:top`).

`xgridcolor`
Default: `RGBAf0(0, 0, 0, 0.12)`
The color of the x grid lines.

`xgridstyle`
Default: `nothing`
The linestyle of the x grid lines.

`xgridvisible`
Default: `true`
Controls if the x grid lines are visible.

`xgridwidth`
Default: `1.0`
The width of the x grid lines.

`xlabel`
Default: `""`
The xlabel string.

`xlabelcolor`
Default: `lift_parent_attribute(scene, :textcolor, :black)`
The color of the xlabel.

`xlabelfont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The font family of the xlabel.

`xlabelpadding`
Default: `3.0`
The padding between the xlabel and the ticks or axis.

`xlabelsize`
Default: `lift_parent_attribute(scene, :fontsize, 16.0f0)`
The font size of the xlabel.

`xlabelvisible`
Default: `true`
Controls if the xlabel is visible.

`xminorgridcolor`
Default: `RGBAf0(0, 0, 0, 0.05)`
The color of the x minor grid lines.

`xminorgridstyle`
Default: `nothing`
The linestyle of the x minor grid lines.

`xminorgridvisible`
Default: `false`
Controls if the x minor grid lines are visible.

`xminorgridwidth`
Default: `1.0`
The width of the x minor grid lines.

`xminortickalign`
Default: `0.0`
The alignment of x minor ticks on the axis spine

`xminortickcolor`
Default: `:black`
The tick color of x minor ticks

`xminorticks`
Default: `IntervalsBetween(2)`
The tick locator for the x minor ticks

`xminorticksize`
Default: `4.0`
The tick size of x minor ticks

`xminorticksvisible`
Default: `false`
Controls if minor ticks on the x axis are visible

`xminortickwidth`
Default: `1.0`
The tick width of x minor ticks

`xpankey`
Default: `AbstractPlotting.Keyboard.x`
The key for limiting panning to the x direction.

`xpanlock`
Default: `false`
Locks interactive panning in the x direction.

`xrectzoom`
Default: `true`
Controls if rectangle zooming affects the x dimension.

`xreversed`
Default: `false`
Controls if the x axis goes rightwards (false) or leftwards (true)

`xscale`
Default: `identity`
The x axis scale

`xtickalign`
Default: `0.0`
The alignment of the xtick marks relative to the axis spine (0 = out, 1 = in).

`xtickcolor`
Default: `RGBf0(0, 0, 0)`
The color of the xtick marks.

`xtickformat`
Default: `AbstractPlotting.automatic`
Format for xticks.

`xticklabelalign`
Default: `AbstractPlotting.automatic`
The horizontal and vertical alignment of the xticklabels.

`xticklabelcolor`
Default: `lift_parent_attribute(scene, :textcolor, :black)`
The color of xticklabels.

`xticklabelfont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The font family of the xticklabels.

`xticklabelpad`
Default: `2.0`
The space between xticks and xticklabels.

`xticklabelrotation`
Default: `0.0`
The counterclockwise rotation of the xticklabels in radians.

`xticklabelsize`
Default: `lift_parent_attribute(scene, :fontsize, 16.0f0)`
The font size of the xticklabels.

`xticklabelspace`
Default: `AbstractPlotting.automatic`
The space reserved for the xticklabels.

`xticklabelsvisible`
Default: `true`
Controls if the xticklabels are visible.

`xticks`
Default: `AbstractPlotting.automatic`
The xticks.

`xticksize`
Default: `6.0`
The size of the xtick marks.

`xticksvisible`
Default: `true`
Controls if the xtick marks are visible.

`xtickwidth`
Default: `1.0`
The width of the xtick marks.

`xtrimspine`
Default: `false`
Controls if the x spine is limited to the furthest tick marks or not.

`xzoomkey`
Default: `AbstractPlotting.Keyboard.x`
The key for limiting zooming to the x direction.

`xzoomlock`
Default: `false`
Locks interactive zooming in the x direction.

`yautolimitmargin`
Default: `(0.05f0, 0.05f0)`
The relative margins added to the autolimits in y direction.

`yaxisposition`
Default: `:left`
The position of the y axis (`:left` or `:right`).

`ygridcolor`
Default: `RGBAf0(0, 0, 0, 0.12)`
The color of the y grid lines.

`ygridstyle`
Default: `nothing`
The linestyle of the y grid lines.

`ygridvisible`
Default: `true`
Controls if the y grid lines are visible.

`ygridwidth`
Default: `1.0`
The width of the y grid lines.

`ylabel`
Default: `""`
The ylabel string.

`ylabelcolor`
Default: `lift_parent_attribute(scene, :textcolor, :black)`
The color of the ylabel.

`ylabelfont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The font family of the ylabel.

`ylabelpadding`
Default: `5.0`
The padding between the ylabel and the ticks or axis.

`ylabelsize`
Default: `lift_parent_attribute(scene, :fontsize, 16.0f0)`
The font size of the ylabel.

`ylabelvisible`
Default: `true`
Controls if the ylabel is visible.

`yminorgridcolor`
Default: `RGBAf0(0, 0, 0, 0.05)`
The color of the y minor grid lines.

`yminorgridstyle`
Default: `nothing`
The linestyle of the y minor grid lines.

`yminorgridvisible`
Default: `false`
Controls if the y minor grid lines are visible.

`yminorgridwidth`
Default: `1.0`
The width of the y minor grid lines.

`yminortickalign`
Default: `0.0`
The alignment of y minor ticks on the axis spine

`yminortickcolor`
Default: `:black`
The tick color of y minor ticks

`yminorticks`
Default: `IntervalsBetween(2)`
The tick locator for the y minor ticks

`yminorticksize`
Default: `4.0`
The tick size of y minor ticks

`yminorticksvisible`
Default: `false`
Controls if minor ticks on the y axis are visible

`yminortickwidth`
Default: `1.0`
The tick width of y minor ticks

`ypankey`
Default: `AbstractPlotting.Keyboard.y`
The key for limiting panning to the y direction.

`ypanlock`
Default: `false`
Locks interactive panning in the y direction.

`yrectzoom`
Default: `true`
Controls if rectangle zooming affects the y dimension.

`yreversed`
Default: `false`
Controls if the y axis goes upwards (false) or downwards (true)

`yscale`
Default: `identity`
The y axis scale

`ytickalign`
Default: `0.0`
The alignment of the ytick marks relative to the axis spine (0 = out, 1 = in).

`ytickcolor`
Default: `RGBf0(0, 0, 0)`
The color of the ytick marks.

`ytickformat`
Default: `AbstractPlotting.automatic`
Format for yticks.

`yticklabelalign`
Default: `AbstractPlotting.automatic`
The horizontal and vertical alignment of the yticklabels.

`yticklabelcolor`
Default: `lift_parent_attribute(scene, :textcolor, :black)`
The color of yticklabels.

`yticklabelfont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The font family of the yticklabels.

`yticklabelpad`
Default: `4.0`
The space between yticks and yticklabels.

`yticklabelrotation`
Default: `0.0`
The counterclockwise rotation of the yticklabels in radians.

`yticklabelsize`
Default: `lift_parent_attribute(scene, :fontsize, 16.0f0)`
The font size of the yticklabels.

`yticklabelspace`
Default: `AbstractPlotting.automatic`
The space reserved for the yticklabels.

`yticklabelsvisible`
Default: `true`
Controls if the yticklabels are visible.

`yticks`
Default: `AbstractPlotting.automatic`
The yticks.

`yticksize`
Default: `6.0`
The size of the ytick marks.

`yticksvisible`
Default: `true`
Controls if the ytick marks are visible.

`ytickwidth`
Default: `1.0`
The width of the ytick marks.

`ytrimspine`
Default: `false`
Controls if the y spine is limited to the furthest tick marks or not.

`yzoomkey`
Default: `AbstractPlotting.Keyboard.y`
The key for limiting zooming to the y direction.

`yzoomlock`
Default: `false`
Locks interactive zooming in the y direction.
