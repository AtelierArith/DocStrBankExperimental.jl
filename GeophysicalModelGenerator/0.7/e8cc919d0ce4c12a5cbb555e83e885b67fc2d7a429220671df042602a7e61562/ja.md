```
surf_new = fit_surface_to_points(surf::CartData, lon_pt::Vector, lat_pt::Vector, depth_pt::Vector)
```

これは、サーフェス `surf` の `depth` 値を、(`lon_pt`,`lat_pt`, `depth_pt`) の最も近いポイントの `depth` 値にフィットさせます。
