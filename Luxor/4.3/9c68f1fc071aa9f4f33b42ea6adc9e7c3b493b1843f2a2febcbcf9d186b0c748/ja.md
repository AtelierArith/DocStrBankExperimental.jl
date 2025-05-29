```
beziersegmentangles(pt1, pt2;
    out = deg2rad(45),
    in  = deg2rad(135),
    l   = 100)
```

`pt1`と`pt2`を結ぶBezierPathSegmentを返し、開始時に`out`の角度、終了時に`in`の角度を作ります。

これは、tikZの`(a) to [out=135, in=45] (b)`描画指示に似ています（ただし、明らかにラジアンで）。

`out`は、`pt1`から出るベジェハンドルが水平と作る角度です。`in`は、前のベジェハンドルから`pt2`を結ぶ線が水平と作る角度です。

この関数は、2つの角度を持つ2つの線の交点を見つけ、フィットするBezierPathSegmentを構築します。

4つの点を通過するBezierPathSegmentを作成する`bezierfrompoints()`関数も参照してください。

### 例

```julia
drawbezierpath(beziersegmentangles(O, O + (100, 0),
    out = deg2rad(45),
    in  = 2π - deg2rad(45)),
    :stroke)
```
