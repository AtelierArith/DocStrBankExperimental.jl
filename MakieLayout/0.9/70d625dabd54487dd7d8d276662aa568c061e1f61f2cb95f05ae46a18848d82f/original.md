LAxis has the following attributes:

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

`targetlimits`
Default: `BBox(0, 100, 0, 100)`
no description

`tellheight`
Default: `true`
Controls if the parent layout can adjust to this element's height

`tellwidth`
Default: `true`
Controls if the parent layout can adjust to this element's width

`title`
Default: `" "`
The axis title string.

`titlealign`
Default: `:center`
The horizontal alignment of the title.

`titlefont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The font family of the title.

`titlegap`
Default: `10.0`
The gap between axis and title.

`titlesize`
Default: `lift_parent_attribute(scene, :fontsize, 20.0f0)`
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
Default: `RGBAf0(0, 0, 0, 0.1)`
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
Default: `" "`
The xlabel string.

`xlabelcolor`
Default: `RGBf0(0, 0, 0)`
The color of the xlabel.

`xlabelfont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The font family of the xlabel.

`xlabelpadding`
Default: `15.0`
The padding between the xlabel and the ticks or axis.

`xlabelsize`
Default: `lift_parent_attribute(scene, :fontsize, 20.0f0)`
The font size of the xlabel.

`xlabelvisible`
Default: `true`
Controls if the xlabel is visible.

`xpankey`
Default: `AbstractPlotting.Keyboard.x`
The key for limiting panning to the x direction.

`xpanlock`
Default: `false`
Locks interactive panning in the x direction.

`xreversed`
Default: `false`
Controls if the x axis goes rightwards (false) or leftwards (true)

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
Default: `(:center, :top)`
The horizontal and vertical alignment of the xticklabels.

`xticklabelcolor`
Default: `RGBf0(0, 0, 0)`
The color of xticklabels.

`xticklabelfont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The font family of the xticklabels.

`xticklabelpad`
Default: `5.0`
The space between xticks and xticklabels.

`xticklabelrotation`
Default: `0.0`
The counterclockwise rotation of the xticklabels in radians.

`xticklabelsize`
Default: `lift_parent_attribute(scene, :fontsize, 20.0f0)`
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
Default: `10.0`
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
Default: `RGBAf0(0, 0, 0, 0.1)`
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
Default: `" "`
The ylabel string.

`ylabelcolor`
Default: `RGBf0(0, 0, 0)`
The color of the ylabel.

`ylabelfont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The font family of the ylabel.

`ylabelpadding`
Default: `15.0`
The padding between the ylabel and the ticks or axis.

`ylabelsize`
Default: `lift_parent_attribute(scene, :fontsize, 20.0f0)`
The font size of the ylabel.

`ylabelvisible`
Default: `true`
Controls if the ylabel is visible.

`ypankey`
Default: `AbstractPlotting.Keyboard.y`
The key for limiting panning to the y direction.

`ypanlock`
Default: `false`
Locks interactive panning in the y direction.

`yreversed`
Default: `false`
Controls if the y axis goes upwards (false) or downwards (true)

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
Default: `(:right, :center)`
The horizontal and vertical alignment of the yticklabels.

`yticklabelcolor`
Default: `RGBf0(0, 0, 0)`
The color of yticklabels.

`yticklabelfont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The font family of the yticklabels.

`yticklabelpad`
Default: `5.0`
The space between yticks and yticklabels.

`yticklabelrotation`
Default: `0.0`
The counterclockwise rotation of the yticklabels in radians.

`yticklabelsize`
Default: `lift_parent_attribute(scene, :fontsize, 20.0f0)`
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
Default: `10.0`
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
