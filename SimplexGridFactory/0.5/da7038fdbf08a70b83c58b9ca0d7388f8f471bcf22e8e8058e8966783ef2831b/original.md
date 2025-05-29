```
bregions!(builder::SimplexGridBuilder,grid, pairs...)
```

Add  boundary facets of `grid`  with region numbers mentioned as first element in `pairs` with region number mentioned as second element of `pairs` to the geometry description. 

Example:

```
bregions!(builder,grid, 1=>2, 3=>5)
```
