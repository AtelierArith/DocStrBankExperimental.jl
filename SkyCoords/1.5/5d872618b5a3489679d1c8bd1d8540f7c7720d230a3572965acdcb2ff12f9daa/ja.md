```
separation(c1::AbstractSkyCoords, c2::AbstractSkyCoords) -> distance
```

2つの天球座標間の角度の分離をラジアンで返します。

角度の分離は、[ヴィンセントの公式](http://en.wikipedia.org/wiki/Great-circle_distance)を使用して計算されます。この公式は、いくつかの代替手段よりもやや複雑で計算コストが高いですが、極や対蹠点を含むすべての距離で安定しています。
