```
decode(gc::Geocoder, point) => NamedTuple{(:country, :country_code, :city), Tuple{String, String, String}}
```

Decode for single point. If processing many points, preferably use `decode(gc, points)` instead of using this method in a loop. 
