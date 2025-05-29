```
filter_walkways(ways::Vector{OpenStreetMapX.Way},
                classes::Dict{String, Int} = OpenStreetMapX.PED_CLASSES;
                levels::Set{Int} = Set(1:length(OpenStreetMapX.PED_CLASSES)))
```

Filters a vector of ways to include only those that are relevant for pedestrian walkways. It considers the presence of a "sidewalk" tag and checks if the corresponding value or the "highway" tag value is present in the specified classes dictionary and levels set.

**Arguments**

  * `ways::Vector{OpenStreetMapX.Way}` : Way's vector
  * `classes` : classes dictionary
  * `levels` : set of levels useful to compare with the way tags
