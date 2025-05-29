```
bezierfrompoints(startpoint::Point,
    pointonline1::Point,
    pointonline2::Point,
    endpoint::Point)
```

4つの点が与えられたとき、`startpoint`から始まり`endpoint`で終わる、すべての4つの点を通るベジェ曲線を返します。返されるBezierPathSegmentの2つの中間点は、曲線が供給された2つの中間点を通るようにするための2つの制御点です。
