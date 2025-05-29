```
SelectClosest(τ::AbstractFloat; distance::Function = absolute_distance)
```

到着したカットは、指定された `distance` 関数に従って最も近い集約に配置されます。許容範囲 `τ` 内に集約がない場合は、空の集約が選択されます。

以下の距離測定が利用可能です

  * [`absolute_distance`](@ref)
  * [`angular_distance`](@ref)
  * [`spatioangular_distance`](@ref)
