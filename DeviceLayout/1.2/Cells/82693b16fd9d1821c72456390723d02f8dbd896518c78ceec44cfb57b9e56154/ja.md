```
text!(c::Cell{S}, str::String, origin::Point=zero(Point{S}), meta::Meta=GDSMeta(); kwargs...) where {S}
```

セル `c` に文字列 `str` をテキスト要素として注釈を付けます。文字列をポリゴンとしてレンダリングするには、[`polytext!`](@ref DeviceLayout.PolyText.polytext!) も参照してください。
