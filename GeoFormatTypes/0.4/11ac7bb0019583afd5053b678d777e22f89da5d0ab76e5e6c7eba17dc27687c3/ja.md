```
ESRIWellKnownText <: AbstractWellKnownText

ESRIWellKnownText(x::String)
ESRIWellKnownText(::CRS, x::String)
ESRIWellKnownText(::Geom, x::String)
```

ESRI標準に従ったウェルノウンテキスト文字列のラッパーです。

これらはCRSまたはジオメトリデータを保持することができます。デフォルトモードは`Unknown`であり、可能な場合はどちらのタイプへの変換が試みられます。特定のタイプが知られている場合は、次のように指定できます：

```julia
crs = ESRIWellKnownText(CRS(), crs_string)
```
