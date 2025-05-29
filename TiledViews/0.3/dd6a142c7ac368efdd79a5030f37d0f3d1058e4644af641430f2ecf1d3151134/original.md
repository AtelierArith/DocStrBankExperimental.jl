```
tile_centers(A, scale=nothing)
```

Returns the relative center coordinates of integer tile centers with respect to the integer center `1 .+ size(A) .÷ 2`  The tuple `scale` is used to multiply the relative position with a physical pixelsize. See also: `eachtilerelpos` for a corresponding iterator
