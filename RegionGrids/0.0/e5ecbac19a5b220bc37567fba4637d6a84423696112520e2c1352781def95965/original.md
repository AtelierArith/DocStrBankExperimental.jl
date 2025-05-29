```
extract(
    odata :: AbstractArray{<:Real},
    ggrd  :: GeneralizedGrid
) -> Array{<:Real}
```

Extracts data from odata, an Array that contains data of a Parent `GeoRegion`, into another Array of dimension N, containing ***only*** within a sub `GeoRegion` we are interested in.

!!! warning
    Please ensure that the 1st dimension is longitude and 2nd dimension is latitude before proceeding. The order of the 3rd and 4th dimensions (when used), however, is not significant.


# Arguments

  * `odata` : An array of dimension N containing gridded data in the region we are interesting in extracting from
  * `ggrd` : A `RegionGrid` containing detailed information on what to extract
