```
add_cluster_layer!(m::KeplerGLMap, table, latitude::Symbol, longitude::Symbol;
    color = colorant"#762A83",
    color_range = [colorant"#762A83",colorant"#AF8DC3",colorant"#E7D4E8",colorant"#D9F0D3",colorant"#7FBF7B",colorant"#1B7837"],
    highlight_color = colorant"#762A83",
    radius_range = [1,40],
    cluster_radius = 20,
    color_aggregation = "count",
    color_field::Symbol = :null,
    color_scale = "quantize",
    opacity = 1.0)
```

Adds a cluster layer to the map `m`, drawing data from `table`.

# Required Arguments

  * `m::KeplerGLMap`: the map that the layer should be added to
  * `table`: a `Tables.jl`-compatible table that contains the data to draw from
  * `latitude::Symbol`: name of the column of `table` that contains the latitude of the points to be aggregated into the hexbin
  * `longitude::Symbol`: name of the column of `table` that contains the longitude of the points to be aggregated into the hexbin

# Optional Arguments

  * `id = randstring(7)`: the string id of the layer
  * `color = colorant"#762A83"`: a `Colors.jl`-compatible color that the hexagons should have (if fixed)
  * `color_range`: a vector of `Colors.jl`-compatible colors. Use `colorant"xyz"` to generate.
  * `color_field::Symbol = :null`: the name of the column of `table` that should be used to color the cluster points
  * `color_scale = "quantize"`: either `"quantize"` or `"quantile"` depending on whether values or quantiles should be used for the color.
  * `highlight_color = colorant"#762A83"`: highlight color.
  * `radius_range = [1,40]`: range for the point radii
  * `cluster_radius = 20`: radius for the clustering
  * `color_aggregation = "count"`: how to aggregate the color
  * `opacity = 1.0`: opacity of the layer, between `0.0` and `1.0`

# Examples

```julia
m = KeplerGL.KeplerGLMap(token)
df = CSV.read("assets/example_data/data.csv", DataFrame)
KeplerGL.add_cluster_layer!(m, df, :Latitude, :Longitude, opacity = 0.5, color_field = :Magnitude, color_scale = "quantile",
    radius_range = [1,40], cluster_radius = 20, color_range = ColorBrewer.palette("BuPu",6), color_aggregation = "count" )
```
