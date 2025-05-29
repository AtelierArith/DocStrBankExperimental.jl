```
setbezierhandles(bezpath::BezierPath;
    angles=[0 .05, -0.1],
    handles=[0.3, 0.3])
```

`bezpath`のすべてのベジェパスセグメントにおけるベジェ制御点の新しい位置を持つ新しいBezierPathを返します。

`angles`は「ハンドル」が線の方向と作る2つの角度です。

`handles`は「ハンドル」の長さです。0.3は典型的な値です。
