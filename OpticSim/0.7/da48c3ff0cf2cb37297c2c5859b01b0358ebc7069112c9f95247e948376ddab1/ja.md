```
HierarchicalImage{T<:Number} <: AbstractArray{T,2}
```

ピクセルの値が設定されるときに動的にメモリを割り当てる画像タイプで、未設定のピクセルの値はゼロであると仮定されます。

これは、通常非常に高解像度であるが、しばしば画像の大部分が空白である[`AbstractOpticalSystem`](@ref)の検出器画像に使用されます。
