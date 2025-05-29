```
detect_gradient_orientation(g₁::AbstractArray, g₂::AbstractArray, orientation_convention::OrientationConvention, args...; kwargs...)
```

最初の（`g₁`）および二番目の（`g₂`）空間次元における勾配が与えられた場合、勾配の方向を返します。この方向は、提供された [`OrientationConvention`](@ref ImageEdgeDetection.OrientationConvention) に従って解釈されます。

# 詳細

勾配の方向をどのように報告するかを指定するには、[`OrientationConvention`](@ref ImageEdgeDetection.OrientationConvention) を提供します。指定しない場合、方向は南の方向から反時計回りに測定されます。これは、ラスタ座標系では、最初の空間次元が画像の下に行くにつれて増加し（つまり南を指す）、二番目の空間次元が画像の右に行くにつれて増加するためです（つまり東を指す）。

標準的なデカルト座標の慣習で方向を解釈したい場合は、参照コンパス方向として東を指定し（`compass_direction = 'E'`）、反時計回りの方向を指定します（`clockwise = false`）。

# 出力

角度の二次元配列を返します。`in_radians = true` の場合、有効な角度は `[0...2π)` の範囲で報告され、それ以外の場合は `[0...360)` の範囲で報告されます。値 `2π` と `360` は、未定義の角度を示すためのセントinelとして使用されます（勾配の大きさがゼロに非常に近かったため）。デフォルトでは、角度は `(abs(g₁) < tol && abs(g₂) < tol)` の場合に未定義とされ、ここで `g₁` と `g₂` は最初と二番目の空間次元における勾配を示し、`tol = sqrt(eps(Float64))`（[`OrientationConvention`](@ref ImageEdgeDetection.OrientationConvention) で定義されているように）です。

関連情報: [`detect_gradient_orientation!`](@ref) ```
