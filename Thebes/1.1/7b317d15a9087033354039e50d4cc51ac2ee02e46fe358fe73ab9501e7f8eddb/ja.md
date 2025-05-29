```
pin(pt::Point3D;
    gfunction = (p3, p2) -> circle(p2, 1, :stroke))
```

現在のLuxor描画に3Dポイントを1つ描画します。

デフォルトのグラフィックは円です。カスタムgfunctionを使用して他のものを定義できます。この関数は2つの引数を取ります：3Dポイントとその2D対点です。

例えば、これは、ポイントが目に近いほど半径が大きくなる円を描きます。

```
pin(p, gfunction = (p3, p2) -> begin
        d = distance(p3, eyepoint())
        circle(p2, rescale(d, 0, 300, 20, 5), :fill)
    end
    )
```

2Dポイントを返します。
