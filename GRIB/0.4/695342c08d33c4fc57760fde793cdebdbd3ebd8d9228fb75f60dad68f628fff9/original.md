```
findmultiple(handle::Message, inlons::Vector{Float64}, inlats::Vector{Float64}; islsm=false)
```

Find the nearest point to each point given.

Setting islsm to true finds the nearest land point and only works when `handle` represents a land-sea-mask. Distance is in kilometers.

# Example

```Julia
lons, lats, values, distances = findmultiple(handle, inlons, inlats)
```
