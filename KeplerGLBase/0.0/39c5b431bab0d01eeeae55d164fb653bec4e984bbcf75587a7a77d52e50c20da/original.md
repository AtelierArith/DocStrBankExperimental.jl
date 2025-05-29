```
add_heatmap_layer!(m::KeplerGLMap, table, latitude::Symbol, longitude::Symbol;
    color = colorant"#762A83",
    color_range = [colorant"#762A83",colorant"#AF8DC3",colorant"#E7D4E8",colorant"#D9F0D3",colorant"#7FBF7B",colorant"#1B7837"],
    weight_field::Symbol = :null,
    weight_scale = "linear",
    highlight_color = colorant"#762A83",
    radius = 0.6,
    opacity = 1.0)
```

Adds a heatmap layer to the map `m`, drawing data from `table`.

# Required Arguments

  * `m::KeplerGLMap`: the map that the layer should be added to
  * `table`: a `Tables.jl`-compatible table that contains the data to draw from
  * `latitude::Symbol`: name of the column of `table` that contains the latitude of the points to be aggregated into the hexbin
  * `longitude::Symbol`: name of the column of `table` that contains the longitude of the points to be aggregated into the hexbin

# Optional Arguments

  * `id = randstring(7)`: the string id of the layer
  * `color = colorant"#762A83"`: a `Colors.jl`-compatible color that the hexagons should have (if fixed)
  * `color_range`: a vector of `Colors.jl`-compatible colors. Use `colorant"xyz"` to generate.
  * `weight_field::Symbol = :null`: the name of the column of `table` that should be used to weigh the heatmap
  * `weight_scale = "linear"`: how the `weight_field` should be translated into weights
  * `highlight_color = colorant"#762A83"`: highlight color.
  * `radius = 10.0`: kernel width of the heatmap
  * `opacity = 1.0`: opacity of the layer, between `0.0` and `1.0`

# Examples

```julia
m = KeplerGL.KeplerGLMap(token)
df = CSV.read("assets/example_data/data.csv", DataFrame)
KeplerGL.add_heatmap_layer!(m, df, :Latitude, :Longitude, opacity = 0.5, weight_field = :Magnitude, weight_scale = "linear",
    radius = 20.0, color_range = ColorBrewer.palette("BuPu",6) )
```
