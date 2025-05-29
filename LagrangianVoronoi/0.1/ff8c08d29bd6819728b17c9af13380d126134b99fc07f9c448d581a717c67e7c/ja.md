```
get_arrow(x::RealVector, y::RealVector, grid::VoronoiGrid)::RealVector
```

`y`から`x`へのベクトルを返します。非周期的なドメインでは`x - y`に等しいです。周期的な長方形の場合、最短のベクトルが返されます。
