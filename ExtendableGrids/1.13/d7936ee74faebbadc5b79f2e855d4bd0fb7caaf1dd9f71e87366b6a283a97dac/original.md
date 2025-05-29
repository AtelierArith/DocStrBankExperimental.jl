```
simplexgrid(grid2d::ExtendableGrid, coordZ; bot_offset=0,cell_offset=0,top_offset=0, bface_offset=0)
```

Create tensor product of 2D  grid and 1D coordinate array.

Cellregions and outer facet regions are taken over from 2D grid and added to `cell_offset` and `bface_offset`, respectively. Top an bottom facet regions are detected from the cell regions and added to `bot_offset` resp. `top_offset`.
