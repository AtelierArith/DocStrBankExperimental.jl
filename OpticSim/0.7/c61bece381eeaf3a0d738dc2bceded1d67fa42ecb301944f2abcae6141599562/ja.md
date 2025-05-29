```
detectorimage(system::AbstractOpticalSystem{T}) -> HierarchicalImage{D}
```

`system`の検出器画像を取得します。`D`は検出器画像のデータ型であり、必ずしもシステム`T`のデータ型と同じであるとは限りません。
