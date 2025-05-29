```
arrow(start::Point, finish::Point, height::Vector, action=:stroke;
    keyword arguments...)
```

`start` と `finish` の間に Bézier 矢印を描画し、制御点は提供された 2 つの `height` 値で定義された想像上のボックスに収まるようにします（`bezierfrompoints()` を参照）。高さの値が異なる符号の場合、矢印は進行中に方向を変えます。

キーワード引数は [`arrow(pt1, pt2, pt3, pt4)`](@ref) と同じです。

### 例

```julia
arrow(pts[1], pts[end], [15, 15],
    decoration = 0.5,
    decorate = () -> text(string(pts[1])))
```
