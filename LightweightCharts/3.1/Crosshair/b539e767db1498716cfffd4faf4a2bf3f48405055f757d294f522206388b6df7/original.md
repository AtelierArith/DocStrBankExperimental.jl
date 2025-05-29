```
CrosshairOptions(; kw...)
```

Structure describing crosshair options.

## Keyword arguments

| Name::Type                        | Default (Possible values) | Description              |
|:--------------------------------- |:------------------------- |:------------------------ |
| `mode::LWC_CROSSHAIR_MODE`        | `LWC_CROSSHAIR_MAGNET`    | Crosshair mode.          |
| `vert_line::CrosshairLineOptions` | `CrosshairLineOptions()`  | Vertical line options.   |
| `horz_line::CrosshairLineOptions` | `CrosshairLineOptions()`  | Horizontal line options. |
