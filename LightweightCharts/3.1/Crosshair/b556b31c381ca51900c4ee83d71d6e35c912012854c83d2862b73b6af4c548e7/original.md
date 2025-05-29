```
CrosshairLineOptions(; kw...)
```

Structure describing a crosshair line (vertical or horizontal).

## Keyword arguments

| Name::Type                        | Default (Possible values)    | Description                                        |
|:--------------------------------- |:---------------------------- |:-------------------------------------------------- |
| `color::String`                   | `'#758696'`                  | Crosshair line color.                              |
| `width::Int64`                    | `1`                          | Crosshair line width.                              |
| `style::LWC_CROSSHAIR_LINE_STYLE` | `LWC_CROSSHAIR_LARGE_DASHED` | Crosshair line style.                              |
| `visible::Bool`                   | `true`                       | Display the crosshair line.                        |
| `label_visible::Bool`             | `true`                       | Display the crosshair label on the relevant scale. |
| `label_background_color::String`  | `'#4c525e'`                  | Crosshair label background color.                  |
