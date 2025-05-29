```
ispointonline(pt::Point, pt1::Point, pt2::Point;
    extended = false,
    atol = 10E-5)
```

点 `pt` が `pt1` と `pt2` の間の直線上にある場合は `true` を返します。

`extended` が false（デフォルト）である場合、点は `pt1` と `pt2` の間の線分上にある必要があります。`extended` が true の場合、点はどちらの方向に延長された線上にあります。
