```
plot_streets(
    city::City, solution::Union{Solution,Nothing}=nothing;
    path::Union{AbstractString,Nothing}=nothing,
    tiles::AbstractString="Cartodb Positron",
    zoom_start::Integer=12,
)
```

Plot a [`City`](@ref) and an optional [`Solution`](@ref) using the Python library [`folium`](https://python-visualization.github.io/folium/), save the result as an HTML file at `path`.

Additional parameters passed to `folium` include:

  * The set of `tiles` used to decorate the map
  * The initial zoom level `zoom_start`

This method is defined in a package extension and requires PythonCall.jl to be loaded.
