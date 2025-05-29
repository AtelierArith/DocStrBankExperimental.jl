```
surf_new = fit_surface_to_points(surf::GeoData, lon_pt::Vector, lat_pt::Vector, depth_pt::Vector)
```

This fits the `depth` values of the surface `surf` to the `depth` value of the closest-by-points in (`lon_pt`,`lat_pt`, `depth_pt`)
