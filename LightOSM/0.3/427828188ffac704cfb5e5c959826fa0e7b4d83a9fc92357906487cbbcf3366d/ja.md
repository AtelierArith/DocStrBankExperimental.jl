```
calculate_location(origin::GeoLocation, heading::Number, distance::Number)
calculate_location(origin::Node, heading::Number, distance::Number)
calculate_location(origin::Vector{GeoLocation}, heading::Vector{<:Number}, distance::Vector{<:Number})
calculate_location(origin::Vector{Node}, heading::Vector{<:Number}, distance::Vector{<:Number})
```

原点 `GeoLocation`(s) または `Node`(s)、進行方向 (度)、および距離 (km) に基づいて次の位置を計算します。

位置は `GeoLocation` として返されます。
