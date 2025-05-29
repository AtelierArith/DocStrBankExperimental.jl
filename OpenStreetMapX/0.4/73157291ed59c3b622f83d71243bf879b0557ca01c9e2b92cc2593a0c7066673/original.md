```
classify_walkways(ways::Vector{OpenStreetMapX.Way},
                  classes::Dict{String, Int} = OpenStreetMapX.PED_CLASSES)
```

Classifies a vector of OpenStreetMapX ways based on their pedestrian attributes. It considers the presence of a "sidewalk" tagand checks if the corresponding value or the "highway" tag value is present in the specified classes dictionary

**Arguments**

  * `ways::Vector{OpenStreetMapX.Way}` : Way's vector
  * `classes` : classes dictionary
