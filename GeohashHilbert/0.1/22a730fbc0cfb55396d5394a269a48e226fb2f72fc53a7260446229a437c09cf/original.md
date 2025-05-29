```
decode_exactly(geohash, bits_per_char)
```

Given a `geohash` string at a specified `bits_per_char`, return the coordinates of the corresponding geohash cell's center and the error margins as a tuple `(lon, lat, lon_err, lat_err)`. That is, each point in the corresponding cell has longitude within `lon` ± `lon_err` and likewise for latitude.

See also: [`rectangle`](@ref)
