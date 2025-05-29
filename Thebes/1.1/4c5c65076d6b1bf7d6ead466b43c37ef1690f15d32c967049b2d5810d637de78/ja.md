```
pin(p3_1::Point3D, p3_2::Point3D;
    gfunction = ((p3_1, p3_2), (p2_1, p2_2)) ->
        line(p2_1, p2_2, :stroke))
```

2つの3Dポイントを描画します。

デフォルトのアクションは、2つのポイントの間に線を描くことです。

gfunctionは、最初の引数として3Dポイントにアクセスでき、2番目の引数として2Dポイントの2つにアクセスできます。

```
pin(p, Point3D(50cos(θ), 50sin(θ), p.z),
    gfunction = (p3s, p2s) -> begin
        line(p2s..., :stroke)
    end)

```

2つの2Dポイントを返します。
