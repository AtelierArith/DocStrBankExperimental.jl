```
set_polygon_hole!(poly :: Polygon_pslg, h :: AbstractArray{Float64,2})
```

Set `poly.hole` appropriately. Input must have dimensions `n_hole`-by-`2`.

!!!     Each hole must be enclosed by segments. Do not place holes on segments.
