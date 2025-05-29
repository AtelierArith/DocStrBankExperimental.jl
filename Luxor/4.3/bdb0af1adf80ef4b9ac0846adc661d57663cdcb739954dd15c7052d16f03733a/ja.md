```
setbezierhandles(bps::BezierPathSegment;
        angles  = [0.05, -0.1],
        handles = [0.3, 0.3])
```

BezierPathSegment `bps` のベジェ制御点の新しい位置を持つ新しい BezierPathSegment を返します。

`angles` は "handles" が線の方向と作る2つの角度です。

`handles` は "handles" の長さです。0.3 は典型的な値です。
