```
locationdata!(data::PopData; longitude::Vector{Union{Missing,String}}, latitude::Vector{Union{Missing,String}})
```

Replaces existing `PopData` geographic coordinate data. Takes **decimal minutes** or **degrees minutes seconds** format as a `Vector` of `String`. Recommended to use `CSV.read` from `CSV.jl` to import your spatial coordinates from a text file.

## Formatting requirements

  * Coordinates as a `String` separated by spaces (`"11 43 41"`) or colons (`"11:43:41"`)
  * Must use negative sign (`"-11 43.52"`) or single-letter cardinal direction (`"11 43.52W"`)
  * Missing data should be coded as the string `"missing"` (can be accomplished with `replace!()`)
  * Can mix colons and spaces (although it's bad practice)

### NOTE

If you read in the coordinate data as 4 vectors (longitude degrees, longitude minutes, latitude degrees, latitude minutes), then the easiest course of action would be to merge them into two vectors of strings (one for longitude, one for latitude):

```
long_string = string.(lat_deg, " ", lat_min)
lat_string = string.(long_deg, " ", long_min)
```

and use these as inputs into `locations!`

### Example

```
ncats = @nancycats;
x = fill("11 22.33W", 237) ; y = fill("-41 31.52", 237)
locationdata!(ncats, longitude = x, latitude = y)
```
