```
GeoData(lld::Tuple{Array,Array,Array})
```

これは、3D座標を持つタプルを入力として持つ場合に`GeoData`構造体を作成します。

# 例

```julia
julia> data = GeoData(lonlatdepth_grid(-10:10,-5:5,0))
GeoData 
  size      : (21, 11, 1)
  lon       ϵ [ -10.0 : 10.0]
  lat       ϵ [ -5.0 : 5.0]
  depth     ϵ [ 0.0 : 0.0]
  fields    : (:Z,)
```
