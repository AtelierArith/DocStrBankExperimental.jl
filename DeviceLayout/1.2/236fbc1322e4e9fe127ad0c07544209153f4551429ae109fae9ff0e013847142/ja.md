```
upperright(ent::AbstractGeometry)
upperright(ents)
```

`ent` または `ents` を囲む矩形の右上隅を返します。この点は `ent` に含まれている必要はありません。

反復可能な `ents` に対しては、幅と高さがゼロの境界矩形を持つエンティティは除外されます。
