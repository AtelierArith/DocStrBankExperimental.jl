IntervalSlider has the following attributes:

`alignmode`
Default: `Inside()`
The align mode of the slider in its parent GridLayout.

`color_active`
Default: `COLOR_ACCENT[]`
The color of the slider when the mouse clicks and drags the slider.

`color_active_dimmed`
Default: `COLOR_ACCENT_DIMMED[]`
The color of the slider when the mouse hovers over it.

`color_inactive`
Default: `RGBf0(0.94, 0.94, 0.94)`
The color of the slider when it is not interacted with.

`halign`
Default: `:center`
The horizontal alignment of the slider in its suggested bounding box.

`height`
Default: `Auto()`
The height setting of the slider.

`horizontal`
Default: `true`
Controls if the slider has a horizontal orientation or not.

`interval`
Default: `(0, 0)`
The current interval of the slider. Don't set this manually, use the function `set_close_to!`.

`linewidth`
Default: `15`
The width of the slider line

`range`
Default: `0:0.01:10`
The range of values that the slider can pick from.

`snap`
Default: `true`
Controls if the buttons snap to valid positions or move freely

`startvalues`
Default: `AbstractPlotting.automatic`
The start values of the slider or the values that are closest in the slider range.

`tellheight`
Default: `true`
Controls if the parent layout can adjust to this element's height

`tellwidth`
Default: `true`
Controls if the parent layout can adjust to this element's width

`valign`
Default: `:center`
The vertical alignment of the slider in its suggested bounding box.

`width`
Default: `Auto()`
The width setting of the slider.
