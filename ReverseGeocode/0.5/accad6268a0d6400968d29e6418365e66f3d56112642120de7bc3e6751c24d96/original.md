```
decode(gc::Geocoder, points) => Array{NamedTuple{(:country, :country_code, :city), Tuple{String, String, String}}}
```

Return country name and city for collection of points. Points should be either an array of staticaly sized arrays  (e.g. StaticArrays) or a Matrix (see NearestNeighbors.jl documentation for details). 

The country and city is determined by the nearest neighbor search in the labelled list of city locations from geonames.org. As such, the results may not be exactly accurate (e.g searches for points close to borders or in the middle of nowhere).

Nearest neighbor search uses the euclidian metric in the space of lat/lon coordinates. 

```
# Example
julia> gc = Geocoder();
julia> ReverseGeocode.decode(gc, [SA[49.5863897, 17.2627342], SA[63.3342550, 12.0280064]])
2-element Array{Tuple{String,String},1}:
 (country="Czechia", country_code="CZ", city="Olomouc")
 (country="Norway", country_code="NO", city="Meråker")
```
