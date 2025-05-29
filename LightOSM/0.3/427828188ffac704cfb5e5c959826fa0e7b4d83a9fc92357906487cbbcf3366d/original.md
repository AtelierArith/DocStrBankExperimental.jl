```
calculate_location(origin::GeoLocation, heading::Number, distance::Number)
calculate_location(origin::Node, heading::Number, distance::Number)
calculate_location(origin::Vector{GeoLocation}, heading::Vector{<:Number}, distance::Vector{<:Number})
calculate_location(origin::Vector{Node}, heading::Vector{<:Number}, distance::Vector{<:Number})
```

Calculates next location(s) given origin `GeoLocation`(s) or `Node`(s), heading(s) (degrees) and distance(s) (km).

Locations are returned as `GeoLocation`s.
