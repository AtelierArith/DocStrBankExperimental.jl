```
CartData(xyz::Tuple{Array,Array,Array})
```

これは、3D座標を入力として持つタプルがある場合に`CartData`構造体を作成します。

# 例

```julia
julia> data = CartData(xyz_grid(-10:10,-5:5,0))
CartData
    size    : (21, 11, 1)
    x       ϵ [ -10.0 km : 10.0 km]
    y       ϵ [ -5.0 km : 5.0 km]
    z       ϵ [ 0.0 km : 0.0 km]
    fields  : (:Z,)
  attributes: ["note"]
```
