```
readGeoRegions(
    fname :: AbstractString
) -> gvec :: Vector{<:GeoRegion}
```

Extract information of GeoRegions from the file defined by `fname`.

# Arguments

  * `fname` : String specifying name + path of the file containing GeoRegion information.

# Returns

  * `gvec` : Vector containing all the GeoRegions in the file `fname`.
