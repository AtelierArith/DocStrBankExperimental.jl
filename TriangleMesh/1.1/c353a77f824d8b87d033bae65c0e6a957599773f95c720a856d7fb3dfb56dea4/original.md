```
set_polygon_region!(poly :: Polygon_pslg, h :: AbstractArray{Float64,2})
```

Set `poly.region` appropriately. Input must have dimensions `n_region`-by-`2`.

!!!     Each region must be enclosed by segments. Do not place regions on segments.
