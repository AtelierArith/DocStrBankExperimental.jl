```
isinbounds(data, I::Tuple) -> Bool
isinbounds(data, I...) -> Bool
```

座標がグリッド内にあるか確認します。通常は[`SetCellRule`](@ref)で使用されます。

[`inbounds`](@ref)とは異なり、[`BoundaryCondition`](@ref)の状態は無視されます。
