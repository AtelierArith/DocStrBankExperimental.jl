```
extract_point_states(system, assembly; prescribed_conditions = Dict())
extract_point_states(x, system, assembly; prescribed_conditions = Dict())
extract_point_states(dx, x, system, assembly; prescribed_conditions = Dict())
```

状態ベクトル `x` と速度ベクトル `dx` に対して、各ポイントに対応する状態変数を返します（[`PointState`](@ref）を参照）。

`prescribed_conditions` が提供されていない場合、すべてのポイント状態変数は、分析で使用される実際のアイデンティティではなく、変位/回転であると見なされます。
