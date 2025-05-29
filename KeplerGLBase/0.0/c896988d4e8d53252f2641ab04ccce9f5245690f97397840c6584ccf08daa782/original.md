```
add_icon_layer!(m, table, latitude::Symbol, longitude::Symbol, icon::Symbol;
    color = colorant"#762A83",
    color_field::Symbol = :null,
    color_range = [colorant"#762A83",colorant"#AF8DC3",colorant"#E7D4E8",colorant"#D9F0D3",colorant"#7FBF7B",colorant"#1B7837"],
    color_scale = "quantize",
    highlight_color = colorant"#762A83",
    altitude::Symbol = :null,
    radius = 10.0,
    radius_fixed = true,
    radius_field::Symbol = :null,
    radius_range = [5.0, 15.0],
    radius_scale = "sqrt",
    opacity = 1.0)
```

Adds an icon layer to the map `m`, drawing data from `table`.

# Required Arguments

  * `m::KeplerGLMap`: the map that the layer should be added to
  * `table`: a `Tables.jl`-compatible table that contains the data to draw from
  * `latitude::Symbol`: name of the column of `table` that contains the latitude of the points
  * `longitude::Symbol`: name of the column of `table` that contains the longitude of the points
  * `icon::Symbol`: name of the column of `table` that contains the strings with symbol names. See below for the list of valid symbol names.

# Optional Arguments

  * `id = randstring(7)`: the string id of the layer
  * `color = colorant"#762A83"`: a `Colors.jl`-compatible color that the points should have (if fixed)
  * `color_field::Symbol = :null`: the name of the column of `table` that should be used to color the points
  * `color_range`: a vector of `Colors.jl`-compatible colors. Use `colorant"xyz"` to generate.
  * `color_scale = "quantize"`: either `"quantize"` or `"quantile"` depending on whether values or quantiles should be used for the color.
  * `highlight_color = colorant"#762A83"`: highlight color.
  * `altitude::Symbol = :null`: the name of the column of `table` that should be used for the altitude of the points
  * `radius = 10.0`: fixed radius value of the points on the map
  * `radius_fixed = true`: whether the radius should be fixed or depend on `radius_field`
  * `radius_field::Symbol = :null`: the name of the column of `table` that should be used for the radius of the points
  * `radius_range = [5.0, 15.0]`: range of the radii of the points
  * `radius_scale = "sqrt"`: how to map `radius_field` into the radius
  * `opacity = 1.0`: opacity of the points, between `0.0` and `1.0`

# Examples

```julia
using Random, Colors
m = KeplerGL.KeplerGLMap(token)
df = CSV.read("assets/example_data/data.csv", DataFrame)
rng = MersenneTwister(12345)
df.icon = rand(rng, ["circle", "plus", "delete"], length(df.Latitude))
KeplerGL.add_icon_layer!(m, df, :Latitude, :Longitude, :icon; color = colorant"black");
```
