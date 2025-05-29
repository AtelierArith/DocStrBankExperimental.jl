```
arc2r(c1::Point, p2::Point, p3::Point; action=:none)
arc2r(c1::Point, p2::Point, p3::Point, action)
```

`c1`を中心とし、`p2`から始まり`p3`で終わる時計回りの円弧を現在のパスに追加します。

`c1`-`p2`は半径を決定します。`p3`が円弧上にない場合、それは位置ではなく円弧の長さの指標としてのみ使用されます。
