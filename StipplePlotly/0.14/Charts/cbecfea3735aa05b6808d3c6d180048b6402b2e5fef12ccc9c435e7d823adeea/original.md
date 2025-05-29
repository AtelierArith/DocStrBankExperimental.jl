```
function watchplot(selector::AbstractString)
```

Generates a js script that forwards plotly events of a DOM element to its respective model fields, e.g. `plot_selected`, `plot_hover`, etc... If no prefix is given, it is taken from the class list which needs to contain at least one entry `'sync_[prefix]'`, e.g `sync_plot`. This function acts on plots that are already present in the UI. It is meant for the rare case of plot-specific event-binding, e.g. in a backend listener.

The normal way forwarding plot events is to call `watchplots()` in `js_mounted()`.
