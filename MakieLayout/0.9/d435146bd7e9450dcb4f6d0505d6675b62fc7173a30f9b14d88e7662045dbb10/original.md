```
labelslider!(scene, label, range; format = string, sliderkw = Dict(), labelkw = Dict(), valuekw = Dict(), layoutkw...)
```

Construct a horizontal GridLayout with a label, a slider and a value label in `scene`.

Returns a `NamedTuple`:

`(slider = slider, label = label, valuelabel = valuelabel, layout = layout)`

Specify a format function for the value label with the `format` keyword. The slider is forwarded the keywords from `sliderkw`. The label is forwarded the keywords from `labelkw`. The value label is forwarded the keywords from `valuekw`. All other keywords are forwarded to the `GridLayout`.

Example:

```
ls = labelslider!(scene, "Voltage:", 0:10; format = x -> "$(x)V")
layout[1, 1] = ls.layout
```
