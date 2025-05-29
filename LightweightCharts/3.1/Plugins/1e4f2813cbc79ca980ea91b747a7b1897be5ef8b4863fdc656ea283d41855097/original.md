```
lwc_trend_line(start_index, start_price, end_index, end_price; kw...) -> LWCPlugin
```

Adds a trend line to the chart starting with `start_index` and `start_price` and ending with `end_index` and `end_price`.

## Keyword arguments

| Name::Type                       | Default (Possible values)     | Description             |
|:-------------------------------- |:----------------------------- |:----------------------- |
| `line_color::String`             | Random color                  | Line color.             |
| `width::Int64`                   | `6`                           | Line width.             |
| `show_labels::Bool`              | `true`                        | Labels visibility.      |
| `label_background_color::String` | `"rgba(255, 255, 255, 0.85)"` | Label background color. |
| `label_text_color::String`       | `"rgb(0, 0, 0)"`              | Label text color.       |
