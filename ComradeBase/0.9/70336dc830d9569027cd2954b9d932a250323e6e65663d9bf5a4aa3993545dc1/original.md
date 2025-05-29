```
domainpoints(k::IntensityMap)
```

Returns the grid the `IntensityMap` is defined as. Note that this is nonallocating since it lazily computes the grid. This is useful for broadcasting a model across an abritrary grid.
