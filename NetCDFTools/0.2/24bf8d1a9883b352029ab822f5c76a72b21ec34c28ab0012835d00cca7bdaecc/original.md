```
earth_dist(x1::Matrix, x2::Matrix; R=6378.388)
earth_dist(p1::Tuple{FT,FT}, x2::AbstractMatrix; R=6378.388) where {FT}
```

```julia
p1 = [110 30; 111 31]
p2 = [113 32; 115 35]
earth_dist(p1, p2)
```
