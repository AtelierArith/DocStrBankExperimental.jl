```
getnearestpointonline(pt1::Point, pt2::Point, startpt::Point)
```

`pt1`と`pt2`を通る直線が与えられたとき、`startpt`から始まる直線が直角でその直線と交わる点を返します。この点は`pt1`と`pt2`の間の直線上にある場合もあればない場合もあります - それを確認するには`ispointonline()`を使用してください。

`perpendicular()`も参照してください。
