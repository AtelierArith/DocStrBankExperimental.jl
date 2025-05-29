```
lwc_vert_line(; kw...) -> LWCPlugin
```

Adds a dynamic tooltip to the chart following the cursor and displaying the values.

## Keyword arguments

| Name::Type                         | Default (Possible values)               | Description                  |
|:---------------------------------- |:--------------------------------------- |:---------------------------- |
| `line_color::String`               | `"rgba(0, 0, 0, 0.2)"`                  | Tooltip line color.          |
| `title::String`                    | `""`                                    | Tooltip title.               |
| `follow_mode::LWC_TOOLTIP_TYPE`    | `LWC_TOOLTIP_TOP` (`LWC_TOOLTIP_TRACK`) | Tooltip Location.            |
| `horizontal_deadzone_width::Int64` | `45`                                    |                              |
| `vertical_deadzone_height::Int64`  | `100`                                   | Horizontal deadzone height.  |
| `vertical_spacing::Int64`          | `20`                                    | Vertical spacing.            |
| `top_offset::Int64`                | `20`                                    | Vertical offset for tooltip. |
