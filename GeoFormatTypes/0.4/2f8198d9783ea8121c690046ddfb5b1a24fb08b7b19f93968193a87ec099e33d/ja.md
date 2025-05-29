```
WellKnownText <: AbstractWellKnownText

WellKnownText(val)
WellKnownText(mode, val)
```

OGC標準に従った、よく知られたテキスト（WKT）v1のラッパーです。これらはCRSまたはジオメトリデータを保持することができます。

これらはCRSまたはジオメトリデータを保持することができます。デフォルトモードは`Mixed()`であり、可能な場合はどちらのタイプへの変換が試みられます。特定のタイプが知られている場合は、次のように指定できます：

```julia
geom = WellKnownText(Geom(), geom_string)
```
