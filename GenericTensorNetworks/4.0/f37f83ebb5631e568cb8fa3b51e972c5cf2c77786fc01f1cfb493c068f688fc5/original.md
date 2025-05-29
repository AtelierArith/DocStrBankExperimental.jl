```
show_landscape(is_neighbor, configurations::TruncatedPoly;
    layer_distance=200,
    config=GraphDisplayConfig(; edge_color="gray", vertex_stroke_color="transparent", vertex_size=5),
    layout_method=:spring,
    optimal_distance=30.0,
    colors=fill("green", K),
    kwargs...)
```

Show the energy landscape of configurations.

### Arguments

  * `is_neighbor`: a function to determine if two configurations are neighbors.
  * `configurations`: a TruncatedPoly object, which is the default output of the [`solve`](@ref) function with [`ConfigsMax`](@ref) property as the argument.

### Keyword arguments

  * `layer_distance`: the distance between layers.
  * `config`: a `LuxorGraphPlot.GraphDisplayConfig` object.
  * `layout_method`: the layout method, either `:spring`, `:stress` or `:spectral`
  * `optimal_distance`: the optimal distance for the layout.
  * `colors`: a vector of colors for each layer.
  * `kwargs...`: other keyword arguments passed to `show_graph`.
