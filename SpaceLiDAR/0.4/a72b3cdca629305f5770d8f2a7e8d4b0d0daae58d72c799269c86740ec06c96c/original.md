```
bounds(granule::ICESat2_Granule)
```

Retrieves the bounding box of the granule.

!!! warning
    This opens the .h5 file, so it is slow.


# Example

```julia
julia> bounds(g)
g = ICESat2_Granule()
```
