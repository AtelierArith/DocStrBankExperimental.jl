```
Theme(source)
```

Construct a theme from the given source, which is either:

  * The name of a [builtin theme](@ref themes).
  * The name of a JSON or YAML file.
  * An iterator of the form `[type => [attr => value, ...], ...]`.

For example, here is a theme which overrides some attributes on all figures, axes, grids and titles:

```julia
Theme([
    "Figure" => [
        "background_fill_color" => "#2F2F2F",
        "border_fill_color" => "#2F2F2F",
        "outline_line_color" => "#444444",
    ],
    "Axis" => [
        "axis_line_color" => nothing,
    ],
    "Grid" => [
        "grid_line_dash" => [6, 4],
        "grid_line_alpha" => 0.3,
    ],
    "Title" => [
        "text_color" => "white",
    ],
])
```

You can apply a theme globally using [`Bokeh.settings!`](@ref) or on a particular plot by wrapping it into a [`Document`](@ref).
