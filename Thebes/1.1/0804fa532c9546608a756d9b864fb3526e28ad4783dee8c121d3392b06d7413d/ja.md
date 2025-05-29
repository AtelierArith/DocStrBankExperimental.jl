```
pin(p3list::Array{Point3D, 1};
    gfunction = (p3list, p2list) ->
        poly(p2list, :stroke, close=true))
```

3Dポイントの配列を描画します。

デフォルトのアクションは、すべてのポイントを通るポリゴンを描画することです。

gfunctionは、最初の引数として3Dポイントにアクセスでき、2番目の引数として2Dポイントを2つ受け取ります。

```
helix = [Point3D(100cos(θ), 100sin(θ), 20θ) for θ in 0:π/12:4π]
a_box = pin(helix, gfunction =
    (p3list, p2list) -> prettypoly(p2list, :stroke)
    )
```

2Dポイントのリストを返します。
