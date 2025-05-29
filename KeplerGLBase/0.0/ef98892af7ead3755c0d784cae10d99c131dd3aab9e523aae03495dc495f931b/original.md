```
add_arc_layer!(m::KeplerGLMap, table, latitude0::Symbol, longitude0::Symbol,
    latitude1::Symbol, longitude1::Symbol;
    color = colorant"#762A83",
    color_field::Symbol = :null,
    color_range = [colorant"#762A83",colorant"#AF8DC3",colorant"#E7D4E8",colorant"#D9F0D3",colorant"#7FBF7B",colorant"#1B7837"],
    color_scale = "quantize",
    highlight_color = colorant"#762A83",
    altitude0::Symbol = :null,
    altitude1::Symbol = :null,
    size_field::Symbol = :null,
    size_range = [1,10],
    size_scale = "linear",
    opacity = 1.0,
    thickness = 2.0,
    elevation_scale = 1)
```

Adds an arc layer to the map `m`, drawing data from `table`.

# Required Arguments

  * `m::KeplerGLMap`: the map that the layer should be added to
  * `table`: a `Tables.jl`-compatible table that contains the data to draw from
  * `latitude0::Symbol`: name of the column of `table` that contains the latitude of the origin of the line
  * `longitude0::Symbol`: name of the column of `table` that contains the longitude of the origin of the line
  * `latitude1::Symbol`: name of the column of `table` that contains the latitude of the endpoint of the line
  * `longitude1::Symbol`: name of the column of `table` that contains the longitude of the endpoint of the line

# Optional Arguments

  * `id = randstring(7)`: the string id of the layer
  * `color = colorant"#762A83"`: a `Colors.jl`-compatible color that the lines should have (if fixed)
  * `color_field::Symbol = :null`: the name of the column of `table` that should be used to color the lines
  * `color_range = [colorant"#762A83",colorant"#AF8DC3",colorant"#E7D4E8",colorant"#D9F0D3",colorant"#7FBF7B",colorant"#1B7837"]`: a vector of `Colors.jl`-compatible colors. Use `colorant"xyz"` to generate.
  * `color_scale = "quantize"`: either `"quantize"` or `"quantile"` depending on whether values or quantiles should be used for the color.
  * `highlight_color = colorant"#762A83"`: highlight color.
  * `altitude0::Symbol = :null`: altitude of the origin of the line.
  * `altitude1::Symbol = :null`: altitude of the endpoint of the line.
  * `size_field::Symbol = :null`: name of the column of `table` that should be used for the line thickness
  * `size_range = [1,10]`: thickness range of the lines
  * `size_scale = "linear"`: how `size_field` should be converted into the actual line thickness
  * `opacity = 1.0`: opacity of the lines
  * `thickness = 2.0`: line thickness, if constant
  * `elevation_scale = 1`: scaling factor for the altitude.

# Examples

```julia
m = KeplerGL.KeplerGLMap(token, center_map=false)
df = CSV.read("assets/example_data/data.csv", DataFrame)
df.Latitude1 = df.Latitude .+ (rand(rng, Float64, length(df.Latitude)) .- 0.5)
df.Longitude1 = df.Longitude .+ 10.0 .* (rand(rng, Float64, length(df.Longitude)) .- 0.5)
KeplerGL.add_arc_layer!(m, df, :Latitude, :Longitude, :Latitude1, :Longitude1,
    opacity = 0.5, color_field = :Magnitude, color_scale = "quantile",
    color_range = ColorBrewer.palette("BuPu",6), thickness = 3)
```
