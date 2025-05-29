```
coords(ga::GeoArray, p::SVector{2,<:Integer}, strategy::AbstractStrategy=Center())
coords(ga::GeoArray, p::Tuple{<:Integer,<:Integer}, strategy::AbstractStrategy=Center())
coords(ga::GeoArray, p::CartesianIndex{2}, strategy::AbstractStrategy=Center())
```

`p`によるセルインデックスの座標を取得します。逆関数については`indices`を参照してください。
