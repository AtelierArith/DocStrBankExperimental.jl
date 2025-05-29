**`Makie.Menu <: Block`**

A drop-down menu with multiple selectable options. You can pass options with the keyword argument `options`.

Options are given as an iterable of elements. For each element, the option label in the menu is determined with `optionlabel(element)` and the option value with `optionvalue(element)`. These functions can be overloaded for custom types. The default is that tuples of two elements are expected to be label and value, where `string(label)` is used as the label, while for all other objects, label = `string(object)` and value = object.

When an item is selected in the menu, the menu's `selection` attribute is set to `optionvalue(selected_element)`. When nothing is selected, that value is `nothing`.

You can set the initial selection by passing one of the labels with the `default` keyword.

## Constructors

```julia
Menu(fig_or_scene; default = nothing, kwargs...)
```

## Examples

Menu with string entries, second preselected:

```julia
menu1 = Menu(fig[1, 1], options = ["first", "second", "third"], default = "second")
```

Menu with two-element entries, label and function:

```julia
funcs = [sin, cos, tan]
labels = ["Sine", "Cosine", "Tangens"]

menu2 = Menu(fig[1, 1], options = zip(labels, funcs))
```

Executing a function when a selection is made:

```julia
on(menu2.selection) do selected_function
    # do something with the selected function
end
```

**Attributes**

(type `?Makie.Menu.x` in the REPL for more information about attribute `x`)

`alignmode`, `cell_color_active`, `cell_color_hover`, `cell_color_inactive_even`, `cell_color_inactive_odd`, `direction`, `dropdown_arrow_color`, `dropdown_arrow_size`, `fontsize`, `halign`, `height`, `i_selected`, `is_open`, `options`, `prompt`, `scroll_speed`, `selection`, `selection_cell_color_inactive`, `tellheight`, `tellwidth`, `textcolor`, `textpadding`, `valign`, `width`
