```
struct GDSMeta <: DeviceLayout.Meta
    layer::Int
    datatype::Int
    GDSMeta() = new(DEFAULT_LAYER, DEFAULT_DATATYPE)
    GDSMeta(l) = new(l, DEFAULT_DATATYPE)
    GDSMeta(l, d) = new(l, d)
end
```

Metadata associated with GDSII format. Default layer and datatype are 0.
