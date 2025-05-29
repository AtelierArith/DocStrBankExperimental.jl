```
NodeSpatIndex(md::MapData, refLLA::LLA = OpenStreetMapX.center(md.bounds); node_range::Number=100.0)
```

`md`内のノードの空間インデックスを作成し、与えられた`node_range`メートルでENU座標の基準として`refLLA`を使用します。
