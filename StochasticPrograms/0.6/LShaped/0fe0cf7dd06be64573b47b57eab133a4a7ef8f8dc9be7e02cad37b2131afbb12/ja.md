```
SortByReference(τ::AbstractFloat; distance::Function = absolute_distance)
```

到着したカットは、指定された `distance` 関数に従って、参照カットとの距離に基づいて集約に配置されます。参照カットに対して許容範囲 `τ` 内でない場合は、[`SelectClosest`](@ref) として動作します。

以下の距離測定が利用可能です

  * [`absolute_distance`](@ref)
  * [`angular_distance`](@ref)
  * [`spatioangular_distance`](@ref)
