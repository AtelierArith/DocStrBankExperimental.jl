```
labelslider!(scene, label, range; format = string, sliderkw = Dict(),
labelkw = Dict(), valuekw = Dict(), value_column_width = automatic, layoutkw...)
```

**`labelslider!` is deprecated, use `SliderGrid` instead**

Construct a horizontal GridLayout with a label, a slider and a value label in `scene`.

Returns a `NamedTuple`:

`(slider = slider, label = label, valuelabel = valuelabel, layout = layout)`

Specify a format function for the value label with the `format` keyword or pass a format string used by `Format.format`. The slider is forwarded the keywords from `sliderkw`. The label is forwarded the keywords from `labelkw`. The value label is forwarded the keywords from `valuekw`. You can set the column width for the value label column with the keyword `value_column_width`. By default, the width is determined heuristically by sampling a few values from the slider range. All other keywords are forwarded to the `GridLayout`.

Example:

```
ls = labelslider!(scene, "Voltage:", 0:10; format = x -> "$(x)V")
layout[1, 1] = ls.layout
```
