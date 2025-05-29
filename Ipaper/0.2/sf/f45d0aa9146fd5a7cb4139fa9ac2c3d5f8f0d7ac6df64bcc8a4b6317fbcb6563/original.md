```
st_location(r::Raster, points::Vector{Tuple{T,T}})
```

return the overlaping indexes `inds`, and corresponding (i,j)

# Examples

```julia
inds, locs = st_location(r, points)
```
