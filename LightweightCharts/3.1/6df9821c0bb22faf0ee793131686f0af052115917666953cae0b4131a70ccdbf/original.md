```
lwc_layout(panels::LWCPanel...; kw...) -> LWCLayout
```

Combines multiple `panels` into a common layout.

## Keyword arguments

| Name::Type            | Default (Possible) values      | Description                                               |
|:--------------------- |:------------------------------ |:--------------------------------------------------------- |
| `name::String`        | `"LightweightCharts ❤️ Julia"` | Layout name (will be displayed in the browser tab title). |
| `sync::Bool`          | `true`                         | Synchronization of chart scrolling.                       |
| `min_height::Integer` | `300`                          | Minimum of layout height in px.                           |
| `resizable::Bool`     | true                           | Enables resize mode of panels.                            |
