```
filter_cycleways(ways::Vector{OpenStreetMapX.Way},
                classes::Dict{String, Int} = OpenStreetMapX.CYCLE_CLASSES;
                levels::Set{Int} = Set(1:length(OpenStreetMapX.CYCLE_CLASSES)))
```

Filters a vector of OpenStreetMapX ways to include only those that are relevant for cycleways. It considers the presence of "bicycle", "cycleway", and "highway" tags and checks if the corresponding values or the constructed class strings are present in the specified classes dictionary and levels set.

**Arguments**

  * `ways::Vector{OpenStreetMapX.Way}` : Way's vector
  * `classes` : classes dictionary
  * `levels` : set of levels useful to compare with the way tags
