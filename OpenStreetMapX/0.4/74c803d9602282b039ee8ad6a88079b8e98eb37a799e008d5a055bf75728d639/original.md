```
classify_cycleways(ways::Vector{OpenStreetMapX.Way},
                   classes::Dict{String, Int} = OpenStreetMapX.CYCLE_CLASSES)
```

Classifies a vector of OpenStreetMapX ways based on their cycleway attributes. It considers the presence of "bicycle", "cycleway", and "highway" tags and checks if the corresponding values or the constructed class strings are present in the specified classes dictionary.

**Arguments**

  * `ways::Vector{OpenStreetMapX.Way}` : Way's vector
  * `classes` : classes dictionary
