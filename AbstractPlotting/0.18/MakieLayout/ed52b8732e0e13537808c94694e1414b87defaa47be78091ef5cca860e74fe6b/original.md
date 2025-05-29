Axis3 has the following attributes:

`alignmode`
Default: `Inside()`
The alignment of the scene in its suggested bounding box.

`aspect`
Default: `(1, 1, 2 / 3)`
Aspects of the 3 axes with each other

`azimuth`
Default: `1.275pi`
The azimuth angle of the camera

`backgroundcolor`
Default: `:transparent`
The background color

`elevation`
Default: `pi / 8`
The elevation angle of the camera

`halign`
Default: `:center`
The horizontal alignment of the scene in its suggested bounding box.

`height`
Default: `nothing`
The height setting of the scene.

`limits`
Default: `(nothing, nothing, nothing)`
The limits that the user has manually set. They are reinstated when calling `reset_limits!` and are set to nothing by `autolimits!`. Can be either a tuple (xlow, xhigh, ylow, high, zlow, zhigh) or a tuple (nothing*or*xlims, nothing*or*ylims, nothing*or*zlims). Are set by `xlims!`, `ylims!`, `zlims!` and `limits!`.

`palette`
Default: `if scene !== nothing && haskey(scene.attributes, :palette)     deepcopy(scene.palette) else     Attributes() end`
Attributes with one palette per key, for example `color = [:red, :green, :blue]`

`perspectiveness`
Default: `0.0`
A number between 0 and 1, where 0 is orthographic, and 1 full perspective

`protrusions`
Default: `30`
The protrusions on the sides of the axis, how much gap space is reserved for labels etc.

`targetlimits`
Default: `FRect3D(Vec3f0(0, 0, 0), Vec3f0(1, 1, 1))`
The limits that the axis tries to set given other constraints like aspect. Don't set this directly, use `xlims!`, `ylims!` or `limits!` instead.

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

`valign`
Default: `:center`
The vertical alignment of the scene in its suggested bounding box.

`viewmode`
Default: `:fitzoom`
The view mode which affects the final projection. `:fit` results in the projection that always fits the limits into the viewport, invariant to rotation. `:fitzoom` keeps the x/y ratio intact but stretches the view so the corners touch the scene viewport. `:stretch` scales separately in both x and y direction to fill the viewport, which can distort the `aspect` that is set.

`width`
Default: `nothing`
The width setting of the scene.

`xautolimitmargin`
Default: `(0.05, 0.05)`
The relative margins added to the autolimits in x direction.

`xgridcolor`
Default: `:gray80`
The x grid color

`xgridvisible`
Default: `true`
Controls if the x grid is visible

`xlabel`
Default: `"x"`
The x label

`xlabelalign`
Default: `AbstractPlotting.automatic`
The x label align

`xlabelcolor`
Default: `lift_parent_attribute(scene, :textcolor, :black)`
The x label color

`xlabelfont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The x label font

`xlabeloffset`
Default: `40`
The x label offset

`xlabelrotation`
Default: `AbstractPlotting.automatic`
The x label rotation

`xlabelsize`
Default: `lift_parent_attribute(scene, :fontsize, 16.0f0)`
The x label size

`xlabelvisible`
Default: `true`
Controls if the x label is visible

`xspinecolor`
Default: `:black`
The x spine color

`xspinesvisible`
Default: `true`
Controls if the x spine is visible

`xspinewidth`
Default: `1`
The x spine width

`xtickcolor`
Default: `:black`
The x tick color

`xtickformat`
Default: `AbstractPlotting.automatic`
The x tick format

`xticklabelcolor`
Default: `lift_parent_attribute(scene, :textcolor, :black)`
The x ticklabel color

`xticklabelfont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The x ticklabel font

`xticklabelsize`
Default: `lift_parent_attribute(scene, :fontsize, 16.0f0)`
The x ticklabel size

`xticklabelsvisible`
Default: `true`
Controls if the x ticklabels are visible

`xticks`
Default: `WilkinsonTicks(5; k_min = 3)`
The x ticks

`xticksvisible`
Default: `true`
Controls if the x ticks are visible

`xtickwidth`
Default: `1`
The x tick width

`xypanelcolor`
Default: `:transparent`
The color of the xy panel

`xypanelvisible`
Default: `true`
Controls if the xy panel is visible

`xzpanelcolor`
Default: `:transparent`
The color of the xz panel

`xzpanelvisible`
Default: `true`
Controls if the xz panel is visible

`yautolimitmargin`
Default: `(0.05, 0.05)`
The relative margins added to the autolimits in y direction.

`ygridcolor`
Default: `:gray80`
The y grid color

`ygridvisible`
Default: `true`
Controls if the y grid is visible

`ylabel`
Default: `"y"`
The y label

`ylabelalign`
Default: `AbstractPlotting.automatic`
The y label align

`ylabelcolor`
Default: `lift_parent_attribute(scene, :textcolor, :black)`
The y label color

`ylabelfont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The y label font

`ylabeloffset`
Default: `40`
The y label offset

`ylabelrotation`
Default: `AbstractPlotting.automatic`
The y label rotation

`ylabelsize`
Default: `lift_parent_attribute(scene, :fontsize, 16.0f0)`
The y label size

`ylabelvisible`
Default: `true`
Controls if the y label is visible

`yspinecolor`
Default: `:black`
The y spine color

`yspinesvisible`
Default: `true`
Controls if the y spine is visible

`yspinewidth`
Default: `1`
The y spine width

`ytickcolor`
Default: `:black`
The y tick color

`ytickformat`
Default: `AbstractPlotting.automatic`
The y tick format

`yticklabelcolor`
Default: `lift_parent_attribute(scene, :textcolor, :black)`
The y ticklabel color

`yticklabelfont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The y ticklabel font

`yticklabelsize`
Default: `lift_parent_attribute(scene, :fontsize, 16.0f0)`
The y ticklabel size

`yticklabelsvisible`
Default: `true`
Controls if the y ticklabels are visible

`yticks`
Default: `WilkinsonTicks(5; k_min = 3)`
The y ticks

`yticksvisible`
Default: `true`
Controls if the y ticks are visible

`ytickwidth`
Default: `1`
The y tick width

`yzpanelcolor`
Default: `:transparent`
The color of the yz panel

`yzpanelvisible`
Default: `true`
Controls if the yz panel is visible

`zautolimitmargin`
Default: `(0.05, 0.05)`
The relative margins added to the autolimits in z direction.

`zgridcolor`
Default: `:gray80`
The z grid color

`zgridvisible`
Default: `true`
Controls if the z grid is visible

`zlabel`
Default: `"z"`
The z label

`zlabelalign`
Default: `AbstractPlotting.automatic`
The z label align

`zlabelcolor`
Default: `lift_parent_attribute(scene, :textcolor, :black)`
The z label color

`zlabelfont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The z label font

`zlabeloffset`
Default: `50`
The z label offset

`zlabelrotation`
Default: `AbstractPlotting.automatic`
The z label rotation

`zlabelsize`
Default: `lift_parent_attribute(scene, :fontsize, 16.0f0)`
The z label size

`zlabelvisible`
Default: `true`
Controls if the z label is visible

`zspinecolor`
Default: `:black`
The z spine color

`zspinesvisible`
Default: `true`
Controls if the z spine is visible

`zspinewidth`
Default: `1`
The z spine width

`ztickcolor`
Default: `:black`
The z tick color

`ztickformat`
Default: `AbstractPlotting.automatic`
The z tick format

`zticklabelcolor`
Default: `lift_parent_attribute(scene, :textcolor, :black)`
The z ticklabel color

`zticklabelfont`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
The z ticklabel font

`zticklabelsize`
Default: `lift_parent_attribute(scene, :fontsize, 16.0f0)`
The z ticklabel size

`zticklabelsvisible`
Default: `true`
Controls if the z ticklabels are visible

`zticks`
Default: `WilkinsonTicks(5; k_min = 3)`
The z ticks

`zticksvisible`
Default: `true`
Controls if the z ticks are visible

`ztickwidth`
Default: `1`
The z tick width
