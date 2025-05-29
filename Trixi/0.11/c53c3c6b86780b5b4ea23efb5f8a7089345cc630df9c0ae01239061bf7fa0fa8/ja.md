```
FluxRotated(numerical_flux)
```

法線ベクトルの方向に `numerical_flux` フラックスを計算するには、解を回転させ、x方向で数値フラックスを計算し、計算されたフラックスを元に戻します。

回転不変な方程式と、方程式特有の関数 [`rotate_to_x`](@ref) および [`rotate_from_x`](@ref) が必要です。
