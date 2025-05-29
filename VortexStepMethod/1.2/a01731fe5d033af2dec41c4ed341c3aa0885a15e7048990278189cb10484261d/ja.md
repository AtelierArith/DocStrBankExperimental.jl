```
@with_kw mutable struct Section
```

先端、後端、および空力特性を持つ翼のセクションを表します。

# フィールド

  * `LE_point::MVec3` = zeros(MVec3): 先端点の座標
  * `TE_point::MVec3` = zeros(MVec3): 後端点の座標
  * `aero_model`::AeroModel = INVISCID: [AeroModel](@ref)
  * `aero_data`::AeroData = nothing: 参照: [AeroData](@ref)
