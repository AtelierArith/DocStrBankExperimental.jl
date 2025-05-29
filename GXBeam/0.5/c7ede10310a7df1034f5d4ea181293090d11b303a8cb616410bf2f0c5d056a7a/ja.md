```
extract_element_state(system, assembly, ielem; prescribed_conditions = Dict())
extract_element_state(x, system, assembly, ielem; prescribed_conditions = Dict())
extract_element_state(dx, x, system, assembly, ielem; prescribed_conditions = Dict())
```

要素 `ielem` に対応する状態変数を返します（状態ベクトル `x` と速度ベクトル `dx` を参照してください）。
