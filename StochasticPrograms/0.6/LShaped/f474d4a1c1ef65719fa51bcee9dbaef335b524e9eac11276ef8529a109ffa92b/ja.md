```
ClusterByReference(τ::AbstractFloat; distance::Function = absolute_distance)
```

バッファカットは、指定された `distance` 関数に従って、基準カットに対して許容範囲 `τ` 内にある場合に集約されます。それ以外の場合はマルチカットとして動作します。

以下の距離測定が利用可能です

  * [`absolute_distance`](@ref)
  * [`angular_distance`](@ref)
  * [`spatioangular_distance`](@ref)
