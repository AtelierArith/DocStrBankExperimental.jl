```
Textbox(parent::Scene; bbox = nothing, kwargs...)
```

Textbox has the following attributes: `alignmode`
Default: `Inside()`
The alignment of the textbox in its suggested bounding box.

`bordercolor`
Default: `RGBf0(0.8, 0.8, 0.8)`
Color of the box border.

`bordercolor_focused`
Default: `COLOR_ACCENT[]`
Color of the box border when focused.

`bordercolor_focused_invalid`
Default: `RGBf0(1, 0, 0)`
Color of the box border when focused and invalid.

`bordercolor_hover`
Default: `COLOR_ACCENT_DIMMED[]`
Color of the box border when hovered.

`borderwidth`
Default: `2.0`
Width of the box border.

`boxcolor`
Default: `:transparent`
Color of the box.

`boxcolor_focused`
Default: `:transparent`
Color of the box when focused.

`boxcolor_focused_invalid`
Default: `RGBAf0(1, 0, 0, 0.3)`
Color of the box when focused.

`boxcolor_hover`
Default: `:transparent`
Color of the box when hovered.

`cornerradius`
Default: `8`
Corner radius of text box.

`cornersegments`
Default: `20`
Corner segments of one rounded corner.

`cursorcolor`
Default: `:transparent`
The color of the cursor.

`defocus_on_submit`
Default: `true`
Controls if the textbox is defocused when a string is submitted.

`displayed_string`
Default: `nothing`
The currently displayed string (for internal use).

`focused`
Default: `false`
If the textbox is focused and receives text input.

`font`
Default: `lift_parent_attribute(scene, :font, "DejaVu Sans")`
Font family.

`halign`
Default: `:center`
The horizontal alignment of the textbox in its suggested bounding box.

`height`
Default: `Auto()`
The height setting of the textbox.

`placeholder`
Default: `"Click to edit..."`
A placeholder text that is displayed when the saved string is nothing.

`reset_on_defocus`
Default: `false`
Controls if the displayed text is reset to the stored text when defocusing the textbox without submitting.

`restriction`
Default: `nothing`
Restricts the allowed unicode input via is_allowed(char, restriction).

`stored_string`
Default: `nothing`
The currently stored string.

`tellheight`
Default: `true`
Controls if the parent layout can adjust to this element's height.

`tellwidth`
Default: `true`
Controls if the parent layout can adjust to this element's width.

`textcolor`
Default: `lift_parent_attribute(scene, :textcolor, :black)`
Text color.

`textcolor_placeholder`
Default: `RGBf0(0.5, 0.5, 0.5)`
Text color for the placeholder.

`textpadding`
Default: `(10, 10, 10, 10)`
Padding of the text against the box.

`textsize`
Default: `lift_parent_attribute(scene, :fontsize, 16.0f0)`
Text size.

`validator`
Default: `str->begin         #= /Users/atelierarith/.julia/packages/AbstractPlotting/2A5iv/src/makielayout/defaultattributes.jl:952 =#         true     end`
Validator that is called with validate_textbox(string, validator) to determine if the current string is valid. Can by default be a RegEx that needs to match the complete string, or a function taking a string as input and returning a Bool. If the validator is a type T (for example Float64), validation will be `tryparse(string, T)`.

`valign`
Default: `:center`
The vertical alignment of the textbox in its suggested bounding box.

`width`
Default: `Auto()`
The width setting of the textbox.
