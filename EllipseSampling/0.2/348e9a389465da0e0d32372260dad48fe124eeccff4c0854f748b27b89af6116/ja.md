```
t_from_arclength_general(arc_len::Float64, e::Ellipse)
```

[`t_from_arclength(arc_len::Float64, e::Ellipse)`](@ref) の一般化されたバージョンで、x軸またはy軸のいずれかが主軸である場合を処理します。

# 引数

  * `arc_len`: 弧の長さ、0.0 と楕円の周囲の間、正の主軸から楕円の周囲に沿って反時計回り。
  * `e`: 楕円を定義する有効な [`EllipseSampling.Ellipse`](@ref) 構造体。
