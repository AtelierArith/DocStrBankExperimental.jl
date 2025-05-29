```
extract_point_state(system, assembly, ipoint; prescribed_conditions = Dict())
extract_point_state(x, system, assembly, ipoint; prescribed_conditions = Dict())
extract_point_state(dx, x, system, assembly, ipoint; prescribed_conditions = Dict())
```

点 `ipoint` に対応する状態変数を返します（状態ベクトル `x` と速度ベクトル `dx` を参照してください）。[`PointState`](@ref) を参照してください。

`prescribed_conditions` が提供されていない場合、すべての点状態変数は、分析で使用される実際のアイデンティティではなく、変位/回転であると見なされます。
