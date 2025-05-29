```
find(near::Nearest, handle::Message, inlon::Float64, inlat::Float64; samepoint=true, samegrid=true)
```

Find the nearest 4 points to the given point sorted by distance.

Setting samepoint and samegrid to true (default) speeds up the calculation but restricts the point and grid, respectively, from changing from call to call. Distance is in kilometers.

# Example

```Julia
Nearest(handle) do near
    lons, lats, values, distances = find(near, handle, inlon, inlat)
end
```
