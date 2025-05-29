```
generate_perimeter_point(norm_distance_on_perimeter::T, x_radius::T, y_radius::T, α::T=0.0, Cx::T=0.0, Cy::T=0.0) where T<:Float64
```

[`generate_perimeter_point(norm_distance_on_perimeter::Float64, e::Ellipse)`](@ref)を呼び出す別の方法で、生成する楕円のパラメータを指定して単一の点を生成します。

# 引数

  * `norm_distance_on_perimeter`: 楕円の周囲における正規化された距離を表す数値 ∈ [0.0,1.0]。値が0.5は楕円の周囲の中間点に対応し、値が0.7は楕円の周囲の70%の位置に対応します。
  * `x_radius`: x軸における楕円の半径（すなわち、回転 `α` がゼロのとき）。
  * `y_radius`: y軸における楕円の半径（すなわち、回転 `α` がゼロのとき）。
  * `α`: 楕円が回転した角度（ラジアン、0から2π）。正の値は反時計回りの回転を表します。デフォルトは `0.0`。
  * `Cx`: 楕円の中心のx座標（x軸における楕円の平行移動）。デフォルトは `0.0`。
  * `Cy`: 楕円の中心のy座標（y軸における楕円の平行移動）。デフォルトは `0.0`。
