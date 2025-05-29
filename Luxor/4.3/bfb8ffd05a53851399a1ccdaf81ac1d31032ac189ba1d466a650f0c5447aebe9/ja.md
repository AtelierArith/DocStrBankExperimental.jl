```
getpath()
```

現在のパスを取得し、`element_type` と `points` オブジェクトの配列である CairoPath オブジェクトを返します。結果を使用して、次のように各エントリをステップスルーして調べることができます。

```julia
o = getpath()
x, y = currentpoint()
for e in o
    if e.element_type == Cairo.CAIRO_PATH_MOVE_TO
        (x, y) = e.points
        move(x, y)
    elseif e.element_type == Cairo.CAIRO_PATH_LINE_TO
        (x, y) = e.points
        # 直線
        line(x, y)
        strokepath()
        circle(x, y, 1, :stroke)
    elseif e.element_type == Cairo.CAIRO_PATH_CURVE_TO
        (x1, y1, x2, y2, x3, y3) = e.points
        # ベジェ制御線
        circle(x1, y1, 1, :stroke)
        circle(x2, y2, 1, :stroke)
        circle(x3, y3, 1, :stroke)
        move(x, y)
        curve(x1, y1, x2, y2, x3, y3)
        strokepath()
        (x, y) = (x3, y3) # 現在の点を更新
    elseif e.element_type == Cairo.CAIRO_PATH_CLOSE_PATH
        closepath()
    else
        error("不明な CairoPathEntry " * repr(e.element_type))
        error("不明な CairoPathEntry " * repr(e.points))
    end
end
```
