```
set_theme!(theme::Symbol)
```

Sets the current theme to be used. The default Deneb's theme (`:default`) sets the following global config:

```json
{
    "view": {"continuousWidth": 300, "continuousHeight": 300, "step": 25},
    "mark": {"tooltip": true}
}
```

The `:default_no_tooltip` theme sets the default size as above, but disables tooltips. The `:empty` theme uses Vega-Lite default empty configuration.

Other available themes are any of the Vega themes: `:dark`, `:excel`, `:fivethirtyeight`, `:ggplot2`, `:googlecharts`, `:latimes`, `:powerbi`, `:quartz`, `:urbaninstitute`, `:vox` (see https://vega.github.io/vega-themes for more info). In this case the `:default` global config will be used.

```
set_theme!(config_theme::Symbol, vega_theme::Symbol)
```

Sets the global config theme (`:default`, `:default_no_tooltip`, `:empty`) and the vega theme (use `vega_theme = :default` for no vega theme).

```
set_theme!(config::NamedTuple, [vega_theme::Symbol])
```

Sets a theme with a user-specified config.
