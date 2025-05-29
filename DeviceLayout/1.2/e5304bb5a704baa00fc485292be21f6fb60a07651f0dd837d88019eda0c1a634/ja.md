```
bounds(geo::AbstractGeometry)
bounds(geo0::AbstractGeometry, geo1::AbstractGeometry, geo::AbstractGeometry...)
bounds(geos)
```

`geo` またはコレクション/イテレータ `geos` の最小バウンディング `Rectangle` を返します。

`geo` が空であるか、範囲がない場合、幅と高さがゼロの長方形が返されます。

複数のエンティティや他の構造への参照を含むコレクションまたは構造の場合、幅と高さがゼロのバウンディングを持つジオメトリは計算から除外されます。
