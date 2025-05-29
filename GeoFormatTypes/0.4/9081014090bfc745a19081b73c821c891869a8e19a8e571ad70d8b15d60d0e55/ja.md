```
WellKnownBinary <: MixedFormat
```

ウェルノウンバイナリ（WKB）オブジェクトのラッパーです。

これらはCRSまたはジオメトリデータを保持することがあります。デフォルトモードは`Unknown`であり、可能な場合はどちらのタイプへの変換が試みられます。特定のタイプが知られている場合は、次のように指定できます：

```julia
crs = WellKnownBinary(CRS(), crs_blob)
```
