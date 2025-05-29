```
labelslidergrid!(scene, labels, ranges; formats = [string],
    sliderkw = Dict(), labelkw = Dict(), valuekw = Dict(),
    value_column_width = automatic, layoutkw...)
```

**`labelslidergrid!` is deprecated, use `SliderGrid` instead**

Construct a GridLayout with a column of label, a column of sliders and a column of value labels in `scene`. The argument values are broadcast, so you can use scalars if you want to keep labels, ranges or formats constant across rows.

Returns a `NamedTuple`:

`(sliders = sliders, labels = labels, valuelabels = valuelabels, layout = layout)`

Specify format functions for the value labels with the `formats` keyword or pass format strings used by `Format.format`. The sliders are forwarded the keywords from `sliderkw`. The labels are forwarded the keywords from `labelkw`. The value labels are forwarded the keywords from `valuekw`. You can set the column width for the value label column with the keyword `value_column_width`. By default, the width is determined heuristically by sampling a few values from the slider ranges. All other keywords are forwarded to the `GridLayout`.

Example:

```julia
ls = labelslidergrid!(scene, ["Voltage", "Ampere"], Ref(0:0.1:100); format = x -> "$(x)V")
layout[1, 1] = ls.layout
```
