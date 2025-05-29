```
pitremoval(dem::Matrix{<:Real})
```

Remove pits from a DEM Array if the center cell of a 3x3 patch is `limit` lower or than the surrounding cells.
