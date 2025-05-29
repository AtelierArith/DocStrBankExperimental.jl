```
add_h3_layer!(m::KeplerGLMap, table, h3::Symbol;
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
    coverage_range = [0,1],
    height_aggregation = "average",
    elevation_percentile = [0,100],
    elevation_scale = 5,
    enable_elevation_zoom_factor = true,
    enable_3d = false)
```

Adds a H3 layer to the map `m`, drawing data from `table`.

# Required Arguments

  * `m::KeplerGLMap`: the map that the layer should be added to
  * `table`: a `Tables.jl`-compatible table that contains the data to draw from
  * `h3::Symbol`: name of the column of `table` that contains the H3 index

# Optional Arguments

  * `id = randstring(7)`: the string id of the layer
  * `color = colorant"#762A83"`: a `Colors.jl`-compatible color that the hexagons should have (if fixed)
  * `color_field::Symbol = :null`: the name of the column of `table` that should be used to color the hexagons
  * `color_range`: a vector of `Colors.jl`-compatible colors. Use `colorant"xyz"` to generate.
  * `color_scale = "quantize"`: either `"quantize"` or `"quantile"` depending on whether values or quantiles should be used for the color.
  * `highlight_color = colorant"#762A83"`: highlight color.
  * `coverage = 0.95`: fraction of the hexagon area that should be covered
  * `opacity = 1.0`: opacity of the hexagons, between `0.0` and `1.0`
  * `height_field::Symbol = :null`: name of the column of `table` that should be used to determine the height of the hexagons
  * `height_scale = "sqrt"`: how `height_field` should be converted into the actual height
  * `height_range = [0,500]`: range of the height of columns
  * `coverage_field = :null`: name of the column of `table` that should be used to determine the coverage of hexagons
  * `coverage_scale = "linear"`: how `coverage_field` should be converted into the actual coverage
  * `coverage_range = [0,1]`: range of the coverage
  * `elevation_scale = 5`: scaling factor for the height
  * `enable_elevation_zoom_factor = true`
  * `enable_3d = false`: nable 3d on the layer

# Examples

```julia
using H3, H3.API
m = KeplerGL.KeplerGLMap(token)
df = CSV.read("assets/example_data/data.csv", DataFrame)
coord = H3.Lib.GeoCoord.(deg2rad.(df.Latitude), deg2rad.(df.Longitude) )
h3 = H3.API.geoToH3.(coord, 5)
df.h3str = H3.API.h3ToString.(h3)
KeplerGL.add_h3_layer!(m, df, :h3str,
    color = colorant"rgb(23,184,190)", color_field = :Magnitude, color_scale = "quantize",
    color_range = ColorBrewer.palette("PRGn", 6));
```
