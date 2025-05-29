```
get_cell_idxs(longlats, cell_geom::Vector; threshold = 1000) -> cell_idxs

get_cell_idxs(longs, lats, cell_geom::Vector; threshold = 1000) -> cell_idxs
```

Return the indices of the closest cells (in `cell_geom`) for each of the longs and lats supplied. If there is no grid cell within `threshold` meters from the point in `cell_geom`, gives an index of 0. `cell_geom` can either be the original geometry (represented as `Box`es), or the longlat geometry (represented as `Quadrangle`s).
