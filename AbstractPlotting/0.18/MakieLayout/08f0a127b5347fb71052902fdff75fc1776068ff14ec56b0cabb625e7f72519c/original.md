```
Menu(parent::Scene; bbox = nothing, kwargs...)
```

Create a drop-down menu with multiple selectable options. You can pass options with the keyword argument `options`. Options are given as an iterable of elements. For each element, the option label in the menu is determined with `optionlabel(element)` and the option value with `optionvalue(element)`. These functions can be overloaded for custom types. The default is that tuples of two elements are expected to be label and value, where `string(label)` is used as the label, while for all other objects, label = `string(object)` and value = object.

When an item is selected in the menu, the menu's `selection` attribute is set to `optionvalue(selected_element)`.

If the menu is located close to the lower scene border, you can change its open direction to `direction = :up`.

# Example

Menu with string entries:

```julia
menu1 = Menu(scene, options = ["first", "second", "third"])
```

Menu with two-element entries, label and function:

```julia
funcs = [sin, cos, tan]
labels = ["Sine", "Cosine", "Tangens"]

menu2 = Menu(scene, options = zip(labels, funcs))
```

Lifting on the selection value:

```julia
on(menu2.selection) do func
    # do something with the selected function
end
```

Menu has the following attributes:

`alignmode`
Default: `Inside()`
The alignment of the menu in its suggested bounding box.

`cell_color_active`
Default: `COLOR_ACCENT[]`
Cell color when active

`cell_color_hover`
Default: `COLOR_ACCENT_DIMMED[]`
Cell color when hovered

`cell_color_inactive_even`
Default: `RGBf0(0.97, 0.97, 0.97)`
Cell color when inactive even

`cell_color_inactive_odd`
Default: `RGBf0(0.97, 0.97, 0.97)`
Cell color when inactive odd

`direction`
Default: `:down`
The opening direction of the menu (:up or :down)

`dropdown_arrow_color`
Default: `(:black, 0.2)`
Color of the dropdown arrow

`dropdown_arrow_size`
Default: `12px`
Size of the dropdown arrow

`halign`
Default: `:center`
The horizontal alignment of the menu in its suggested bounding box.

`height`
Default: `Auto()`
The height setting of the menu.

`i_selected`
Default: `0`
Index of selected item

`is_open`
Default: `false`
Is the menu showing the available options

`options`
Default: `["no options"]`
The list of options selectable in the menu. This can be any iterable of a mixture of strings and containers with one string and one other value. If an entry is just a string, that string is both label and selection. If an entry is a container with one string and one other value, the string is the label and the other value is the selection.

`prompt`
Default: `"Select..."`
The default message prompting a selection when i == 0

`selection`
Default: `nothing`
Selected item value

`selection_cell_color_inactive`
Default: `RGBf0(0.94, 0.94, 0.94)`
Selection cell color when inactive

`tellheight`
Default: `true`
Controls if the parent layout can adjust to this element's height

`tellwidth`
Default: `true`
Controls if the parent layout can adjust to this element's width

`textcolor`
Default: `:black`
Color of entry texts

`textpadding`
Default: `(10, 10, 10, 10)`
Padding of entry texts

`textsize`
Default: `lift_parent_attribute(scene, :fontsize, 16.0f0)`
Font size of the cell texts

`valign`
Default: `:center`
The vertical alignment of the menu in its suggested bounding box.

`width`
Default: `nothing`
The width setting of the menu.
