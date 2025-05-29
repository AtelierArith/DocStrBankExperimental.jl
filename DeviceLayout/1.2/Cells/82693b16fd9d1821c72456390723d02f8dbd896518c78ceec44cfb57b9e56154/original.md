```
text!(c::Cell{S}, str::String, origin::Point=zero(Point{S}), meta::Meta=GDSMeta(); kwargs...) where {S}
```

Annotate cell `c` with string `str` as a text element. See also [`polytext!`](@ref DeviceLayout.PolyText.polytext!) for rendering strings as polygons.
