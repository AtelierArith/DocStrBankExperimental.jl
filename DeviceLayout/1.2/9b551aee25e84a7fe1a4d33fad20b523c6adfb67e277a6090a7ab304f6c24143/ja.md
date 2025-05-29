```
struct GDSMeta <: DeviceLayout.Meta
    layer::Int
    datatype::Int
    GDSMeta() = new(DEFAULT_LAYER, DEFAULT_DATATYPE)
    GDSMeta(l) = new(l, DEFAULT_DATATYPE)
    GDSMeta(l, d) = new(l, d)
end
```

GDSIIフォーマットに関連付けられたメタデータ。デフォルトのレイヤーとデータタイプは0です。
