```
st_location(r::Raster, points::Vector{Tuple{T,T}})
```

重複するインデックス `inds` と対応する (i,j) を返します。

# 例

```julia
inds, locs = st_location(r, points)
```
