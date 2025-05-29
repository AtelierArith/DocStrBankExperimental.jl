```
EllipticalArc(x1::Real, y1::Real, x2::Real, y2::Real, rx::Real, ry::Real, ϕ::Real, largearc::Bool, sweepflag::Bool)
```

エリプティカルアークをエンドポイントパラメータ化を使用して構築します。

`x1, y1` は開始点で、`x2, y2` は終点、`rx` と `ry` は2つの楕円の半径です。`ϕ` は `rx` と x 軸の角度です。

通常、これらの楕円パラメータが与えられた場合、2つの点の間に4つのアークを構築できます。そのうちの1つは2つのブールフラグを使用して選択されます：

`largearc === true` の場合、アークは180度より長くなります。`sweepflag === true` の場合、アークは増加する角度を通過します。
