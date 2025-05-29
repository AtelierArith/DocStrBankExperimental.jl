```
interdigit!(c::AbstractCoordinateSystem{T}, width, length, fingergap, fingeroffset, npairs::Integer,
    skiplast, meta::Meta=GDSMeta(0,0)) where {T}
```

指が交互に配置された指を作成します。例えば、集中型素子キャパシタ用です。

  * `width`: 指の幅
  * `length`: 指の長さ
  * `fingeroffset`: 指の端でのxオフセット
  * `fingergap`: 指の間の隙間
  * `npairs`: 指の数
  * `skiplast`: 最後の指をスキップしますか？奇数の数を残しますか？
