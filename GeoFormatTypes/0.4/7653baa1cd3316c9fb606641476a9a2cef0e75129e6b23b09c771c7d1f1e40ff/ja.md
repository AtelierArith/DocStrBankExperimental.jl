```
WellKnownText2 <: AbstractWellKnownText

WellKnownText2(val)
WellKnownText2(mode, val)
```

OGC標準に従った、よく知られたテキストv2オブジェクトのラッパーです。

これらはCRSまたはジオメトリデータを保持することができます。デフォルトモードは`Unknown()`であり、可能な場合はどちらのタイプへの変換が試みられます。特定のタイプが知られている場合は、次のように指定できます：

```julia
crs = WellKnownText2(CRS(), crs_string)
```
