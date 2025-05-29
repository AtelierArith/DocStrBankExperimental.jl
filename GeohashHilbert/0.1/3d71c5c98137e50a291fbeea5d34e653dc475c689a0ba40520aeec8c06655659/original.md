```
decode(geohash, bits_per_char = 2)
```

Given a `geohash` string at a specified `bits_per_char`, return the coordinates of the corresponding geohash cell's center as a tuple `(lon, lat)`.

See also: [`decode_exactly`](@ref)
