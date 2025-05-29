```
set_polygon_point_marker!(poly :: Polygon_pslg, pm :: AbstractArray{Int,2})
```

Set `poly.point_marker` appropriately. Input must have dimensions `n_point`-by-`n_point_marker`. `n_point_marker` can be 1 or 0.
