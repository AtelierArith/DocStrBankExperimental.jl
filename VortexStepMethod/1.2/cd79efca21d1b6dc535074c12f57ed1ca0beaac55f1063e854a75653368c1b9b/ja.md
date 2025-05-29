```
add_section!(wing::Wing, LE_point::PosVector, TE_point::PosVector, 
             aero_model, aero_data::AeroData=nothing)
```

翼に新しいセクションを追加します。

# 引数:

  * wing::Wing: セクションを追加する[Wing](@ref)
  * LE_point::PosVector: 前縁側の点の[PosVector](@ref)
  * TE_point::PosVector: 後縁側の点の[PosVector](@ref)
  * `aero_model`::AeroModel: [AeroModel](@ref)
  * `aero_data`::AeroData: [AeroData](@ref)を参照してください
