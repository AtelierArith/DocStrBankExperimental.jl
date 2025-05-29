```
add_grid_layer!(m::KeplerGLMap, table, latitude::Symbol, longitude::Symbol;
    color = colorant"#762A83",
    color_field::Symbol = :null,
    color_range = [colorant"#762A83",colorant"#AF8DC3",colorant"#E7D4E8",colorant"#D9F0D3",colorant"#7FBF7B",colorant"#1B7837"],
    color_scale = "quantile",
    color_aggregation = "average",
    highlight_color = colorant"#762A83",
    radius = 0.6,
    coverage = 0.95,
    resolution = 8,
    opacity = 1.0,
    height_field::Symbol = :null,
    height_scale = "sqrt",
    height_percentile = [0,100],
    height_aggregation = "average",
    elevation_percentile = [0,100],
    elevation_scale = 5,
    enable_elevation_zoom_factor = true,
    enable_3d = false)
```

Adds a grid layer to the map `m`, drawing data from `table`.

# Required Arguments

  * `m::KeplerGLMap`: the map that the layer should be added to
  * `table`: a `Tables.jl`-compatible table that contains the data to draw from
  * `latitude::Symbol`: name of the column of `table` that contains the latitude of the points to be aggregated into the hexbin
  * `longitude::Symbol`: name of the column of `table` that contains the longitude of the points to be aggregated into the hexbin

# Optional Arguments

  * `id = randstring(7)`: the string id of the layer
  * `color = colorant"#762A83"`: a `Colors.jl`-compatible color that the hexagons should have (if fixed)
  * `color_field::Symbol = :null`: the name of the column of `table` that should be used to color the hexagons
  * `color_range`: a vector of `Colors.jl`-compatible colors. Use `colorant"xyz"` to generate.
  * `color_scale = "quantize"`: either `"quantize"` or `"quantile"` depending on whether values or quantiles should be used for the color.
  * `highlight_color = colorant"#762A83"`: highlight color.
  * `radius = 10.0`: fixed radius value of the hexagons on the map
  * `coverage = 0.95`: fraction of the hexagon area that should be covered
  * `resolution = 8`
  * `opacity = 1.0`: opacity of the hexagons, between `0.0` and `1.0`
  * `height_field::Symbol = :null`: name of the column of `table` that should be used to determine the height of the hexagons
  * `height_scale = "sqrt"`: how `height_field` should be converted into the actual height
  * `height_percentile = [0,100]`:
  * `height_aggregation = "average"`:
  * `elevation_percentile = [0,100]`:
  * `elevation_scale = 5`: scaling factor for the height
  * `enable_elevation_zoom_factor = true`
  * `enable_3d = false`: nable 3d on the layer

# Examples

```julia
m = KeplerGL.KeplerGLMap(token)
df = CSV.read("assets/example_data/data.csv", DataFrame)
KeplerGL.add_grid_layer!(m, df, :Latitude, :Longitude, opacity = 0.5, color_field = :Magnitude, color_scale = "quantile",
    radius = 20.0, color_range = ColorBrewer.palette("BuPu",6), color_aggregation = "average", coverage = 0.95,
    height_field = :Magnitude )
```
