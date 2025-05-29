```
transformation(c::GeometryStructure, d::GeometryReference, e::GeometryReference, f::GeometryReference...)
```

幾何構造 `c` がその参照のツリー内に [`GeometryReference`](@ref) `last(f)` を含んでいる場合、この関数は `Transformations.ScaledIsometry` オブジェクトを返し、`last(f)` の座標系から `c` の座標系に変換することができます。このメソッドは、中間の `GeometryReference` を明示的に指定したい場合に必要です。

例えば、座標系 A が B1 と B2 を参照し、両方が C を参照する座標系の階層があるとします。概念的には、次のようになります：

```
a -- b1 -- c
  \      /
   \ b2 /
```

座標系 C は、B1 と B2 の両方によって参照されているため、座標系 A 内の 2 つの場所に現れます。B2 を介して C の座標系を取得する必要がある場合、単に `transform(coordinatesystemA, coordsysrefC)` を使うのではなく、`transformation(coordinatesystemA, coordsysrefB2, coordsysrefC)` を使用する必要があります。なぜなら、後者は B1 を介して C への最初のパスを単に取るだけだからです。 ```
