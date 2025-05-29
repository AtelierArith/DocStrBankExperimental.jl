```
    OrientationConvention(; compass_direction::AbstractChar = 'S', is_clockwise::Bool = false, in_radians = true, tol = sqrt(eps(Float64)))
```

`detect_gradient_orientation` の角度の意味（勾配の向き）を決定するための座標系のコンテキストを指定します。

# 詳細

勾配の向きをどのように報告するかを指定できます。デフォルトでは、向きは南の方向から反時計回りに測定されます。これは、ラスタ座標系では、最初の空間次元が画像の下に行くにつれて増加し（すなわち南を指す）、2番目の空間次元が画像の右に移動するにつれて増加するためです（すなわち東を指す）。

標準的なデカルト座標系の慣習で向きを解釈したい場合は、参照コンパス方向を東（`compass_direction = 'E'`）として指定し、反時計回りの方向（`clockwise = false`）を指定します。

`in_radians = true` の場合、有効な角度は `[0...2π)` の範囲で報告されます。そうでない場合は `[0...360)` の範囲で報告されます。値 `2π` と `360` は、未定義の角度を示すためのセントinelとして使用されます（勾配の大きさがゼロに非常に近かったため）。デフォルトでは、角度は `(abs(g₁) < tol && abs(g₂) < tol)` の場合に未定義とされ、ここで `g₁` と `g₂` は最初と2番目の空間次元の勾配を示し、`tol = sqrt(eps(Float64))` です。

# 例

```julia

using TestImages, FileIO, ImageView, ImageEdgeDetection, ImageFiltering

img =  testimage("mandril_gray")

# 最初と2番目の空間次元の勾配
g₁, g₂ = imgradients(img, KernelFactors.scharr)

# 角度が正のx軸から反時計回りに測定される標準的なデカルト座標系に関して角度を解釈します。

orientation_convention = OrientationConvention(in_radians = true,
                                               is_clockwise = false,
                                               compass_direction = 'E')
angles = detect_gradient_orientation(g₁, g₂, orientation_convention)

```
