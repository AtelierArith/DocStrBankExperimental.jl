```
box(g::OceanGrid, i, j, k)
```

Accesses the individual box of `g::OceanGrid` at index `(i,j,k)`. Each grid can be looped over, where the `OceanGridBox` are the elements of the grid. This useful to investigate specific boxes in the grid.
