```
set_polygon_segment_marker!(poly :: Polygon_pslg, sm :: AbstractArray{Int,1})
```

Set `poly.segment_marker` appropriately. Input must have dimensions `n_segment`-by-`1`. If not set every segemnt will have marker equal to 1.
