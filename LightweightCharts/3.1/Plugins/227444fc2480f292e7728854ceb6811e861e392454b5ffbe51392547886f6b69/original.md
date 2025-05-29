```
lwc_vert_line(index::Int64; kw...) -> LWCPlugin
```

Adds a vertical line based on `index` to the chart.

## Keyword arguments

| Name::Type                       | Default (Possible values) | Description                 |
|:-------------------------------- |:------------------------- |:--------------------------- |
| `label_text::String`             | `""`                      | Vertical line label.        |
| `width::Float64`                 | `3.0`                     | Vertical line width.        |
| `color::String`                  | Random color              | Color of the vertical line. |
| `label_background_color::String` | Random color              | Label background color.     |
| `label_text_color::String`       | `"white"`                 | Label text color.           |
| `show_label::Bool`               | `false`                   | Label visibility.           |
