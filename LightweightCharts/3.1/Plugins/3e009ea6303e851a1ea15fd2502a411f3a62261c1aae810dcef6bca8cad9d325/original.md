```
lwc_vert_line(; kw...) -> LWCPlugin
```

Adds a dynamic tooltip to the chart following the cursor and displaying the values (and their change, while holding down the mouse button).

## Keyword arguments

| Name::Type           | Default (Possible values) | Description                  |
|:-------------------- |:------------------------- |:---------------------------- |
| `line_color::String` | `"rgba(0, 0, 0, 0.2)"`    | Line color.                  |
| `show_time::Bool`    | `false`                   | Detailed time display.       |
| `top_offset::Int64`  | `20`                      | Vertical offset for tooltip. |
