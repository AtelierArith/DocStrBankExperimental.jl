```
function cross_section_points(P::GeoData; Depth_level=nothing, Lat_level=nothing, Lon_level=nothing, Start=nothing, End=nothing, section_width=50 )
```

選択した平面に別々の点の投影を作成します（GeoDataオブジェクトとして保存されます）。最大距離がsection_widthの点のみが考慮されます。
