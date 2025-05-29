```
t_from_arclength_general(arc_len::T, a::T, b::T, x_radius::T, y_radius::T) where T<:Float64
```

[`t_from_arclength(arc_len::T, a::T, b::T) where T<:Float64`](@ref) の一般化されたバージョンで、x軸またはy軸のいずれかが主軸である場合を処理します。

# 引数

  * `arc_len`: 弧の長さ、0.0と楕円の周囲の間、正の主軸から楕円の周囲に沿って反時計回り。
  * `a`: 楕円の主軸の半径。
  * `b`: 楕円の副軸の半径。
  * `x_radius`: x軸における楕円の半径（すなわち、回転 `α` がゼロのとき）。
  * `y_radius`: y軸における楕円の半径（すなわち、回転 `α` がゼロのとき）。
